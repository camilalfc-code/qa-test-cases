# Casos de Uso — SQL em Testes de Software
Cenários práticos de como um analista de QA usa SQL no dia a dia para validar dados e investigar problemas.

## Caso 1 — Validar cadastro de usuário

### Objetivo
Situação: após preencher e submeter o formulário de cadastro na interface, verificar se os dados foram gravados corretamente.

### Passos
Buscar o usuário pelo e-mail informado no cadastro
SELECT id, nome, email, status, data_criacao
FROM usuarios
WHERE email = 'camila@teste.com';

### O que validar
Nome gravado sem caracteres estranhos

E-mail em letras minúsculas (ou conforme regra do sistema)

Status = 'ativo' (ou o valor esperado para novo cadastro)

Data de criação corresponde ao momento do teste


## Caso 2 — Verificar se senha foi criptografada

### Objetivo
Situação: o sistema não deve armazenar senha em texto puro (plain text). Verificar se está sendo criptografada.

### Passos
SELECT nome, senha FROM usuarios WHERE email = 'camila@teste.com';

### O que validar
O campo senha deve conter um hash (sequência longa de caracteres aleatórios)

Se mostrar a senha digitada em texto puro — isso é um bug de segurança grave


## Caso 3 — Confirmar atualização de dados

### Objetivo
Situação: o usuário alterou o endereço no perfil. Verificar se a alteração foi salva.

### Passos
-- Antes da alteração — anotar o valor atual
SELECT endereco FROM clientes WHERE id = 42;

-- Após a alteração — comparar com o novo valor
SELECT endereco, data_atualizacao FROM clientes WHERE id = 42;

### O que validar
Novo endereço gravado corretamente

Campo data_atualizacao foi atualizado com o timestamp atual


## Caso 4 — Validar exclusão de registro

### Objetivo
Situação: o usuário deletou um item. Verificar se foi realmente removido (ou apenas marcado como inativo, dependendo da regra do sistema).

### Passos
-- Verificar se o registro ainda existe
SELECT * FROM produtos WHERE id = 15;

-- Se o sistema usa "soft delete" (não apaga, só desativa)
SELECT id, nome, status, deletado_em FROM produtos WHERE id = 15;

### O que validar
Se exclusão física: nenhum resultado deve ser retornado

Se soft delete: status = 'inativo' e deletado_em preenchido


## Caso 5 — Checar regra de negócio: desconto por categoria

### Objetivo
Situação: o sistema aplica 10% de desconto para clientes da categoria "premium". Validar se a regra está sendo aplicada corretamente.

### Passos
-- Buscar pedidos de clientes premium e verificar desconto
SELECT pedidos.id, clientes.categoria, pedidos.valor_total, pedidos.desconto
FROM pedidos
JOIN clientes ON pedidos.cliente_id = clientes.id
WHERE clientes.categoria = 'premium'
ORDER BY pedidos.data_criacao DESC
LIMIT 10;

### O que validar
Todos os registros com categoria = 'premium' devem ter desconto = 10

Se algum registro premium tiver desconto = 0 — bug na regra de negócio


## Caso 6 — Identificar dados duplicados

### Objetivo
Situação: suspeita de que o sistema está gravando pedidos duplicados em situações de duplo clique ou lentidão.

### Passos
-- Buscar combinações de cliente + valor + data que aparecem mais de uma vez
SELECT cliente_id, valor_total, DATE(data_criacao), COUNT(*) as total
FROM pedidos
GROUP BY cliente_id, valor_total, DATE(data_criacao)
HAVING COUNT(*) > 1;

### O que validar
Nenhum resultado = sem duplicatas

Se retornar registros = possível bug de duplicação


## Caso 7 — Validar campos obrigatórios

### Objetivo
Situação: o sistema tem campos obrigatórios que deveriam ser bloqueados na interface. Verificar se algum conseguiu ser gravado vazio mesmo assim.

### Passos
-- Verificar campos críticos que não deveriam ser NULL
SELECT id, nome, email, cpf
FROM clientes
WHERE nome IS NULL
   OR email IS NULL
   OR cpf IS NULL;

### O que validar
Nenhum resultado = validação funcionando corretamente
Se retornar registros = a validação do campo obrigatório tem falha


Repositório de estudos — Camila Lopes | QA em formação
