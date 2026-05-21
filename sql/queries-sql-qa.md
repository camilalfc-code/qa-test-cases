# Queries SQL para QA — Validação de Dados

Consultas SQL organizadas por tipo, com foco em validação de dados e apoio a testes de software.

---

## 1. SELECT — Buscar e visualizar registros

A query mais básica. Usada para verificar se os dados foram salvos corretamente após uma ação no sistema.

```sql
-- Buscar todos os usuários cadastrados
SELECT * FROM usuarios;

-- Buscar apenas campos específicos (mais eficiente)
SELECT id, nome, email, status FROM usuarios;
```

**Uso em QA:** após cadastrar um usuário na interface, confirmar se os dados foram gravados corretamente no banco.

---

## 2. WHERE — Filtrar registros

Filtra resultados por condição. Essencial para isolar o dado que você quer validar.

```sql
-- Buscar usuário específico por e-mail
SELECT * FROM usuarios WHERE email = 'teste@exemplo.com';

-- Buscar pedidos com status específico
SELECT * FROM pedidos WHERE status = 'pendente';

-- Buscar registros de uma data específica
SELECT * FROM logs WHERE data_criacao = '2025-05-01';
```

**Uso em QA:** validar se um registro específico foi criado, atualizado ou removido corretamente.

---

## 3. AND / OR — Múltiplas condições

Combinam condições para filtros mais precisos.

```sql
-- Buscar usuários ativos E com perfil administrador
SELECT * FROM usuarios WHERE status = 'ativo' AND perfil = 'admin';

-- Buscar pedidos cancelados OU com erro de pagamento
SELECT * FROM pedidos WHERE status = 'cancelado' OR status = 'erro_pagamento';
```

**Uso em QA:** validar combinações de campos — por exemplo, verificar se um desconto foi aplicado apenas para clientes que atendem a dois critérios ao mesmo tempo.

---

## 4. COUNT — Contar registros

Conta quantos registros atendem a uma condição.

```sql
-- Contar total de usuários cadastrados
SELECT COUNT(*) FROM usuarios;

-- Contar pedidos com status 'concluído'
SELECT COUNT(*) FROM pedidos WHERE status = 'concluido';

-- Contar usuários por perfil
SELECT perfil, COUNT(*) FROM usuarios GROUP BY perfil;
```

**Uso em QA:** verificar se a quantidade de registros está correta após uma importação, cadastro em massa ou deleção.

---

## 5. JOIN — Cruzar dados de tabelas diferentes

Combina dados de duas ou mais tabelas. Muito útil para validar relacionamentos entre entidades.

```sql
-- Buscar pedidos com nome do cliente (tabela pedidos + tabela clientes)
SELECT pedidos.id, clientes.nome, pedidos.valor, pedidos.status
FROM pedidos
JOIN clientes ON pedidos.cliente_id = clientes.id;

-- Buscar itens de um pedido com nome do produto
SELECT pedidos.id, produtos.nome, itens_pedido.quantidade
FROM itens_pedido
JOIN pedidos ON itens_pedido.pedido_id = pedidos.id
JOIN produtos ON itens_pedido.produto_id = produtos.id;
```

**Uso em QA:** validar se os relacionamentos entre tabelas estão corretos — por exemplo, se um pedido está vinculado ao cliente certo.

---

## 6. NULL — Identificar campos vazios

Verifica campos sem valor preenchido — um dos erros mais comuns em sistemas.

```sql
-- Buscar usuários sem e-mail cadastrado
SELECT * FROM usuarios WHERE email IS NULL;

-- Buscar pedidos sem data de entrega definida
SELECT * FROM pedidos WHERE data_entrega IS NULL;

-- Buscar registros COM valor preenchido (NOT NULL)
SELECT * FROM usuarios WHERE telefone IS NOT NULL;
```

**Uso em QA:** identificar campos obrigatórios que foram gravados vazios, o que indica falha na validação do sistema.

---

## 7. ORDER BY — Ordenar resultados

Organiza os resultados por um campo, facilitando a análise.

```sql
-- Listar pedidos do mais recente para o mais antigo
SELECT * FROM pedidos ORDER BY data_criacao DESC;

-- Listar usuários em ordem alfabética
SELECT nome, email FROM usuarios ORDER BY nome ASC;
```

**Uso em QA:** facilita a localização do registro mais recente após um teste, sem precisar procurar manualmente.

---

## 8. LIKE — Busca parcial de texto

Útil para encontrar registros por parte do valor.

```sql
-- Buscar usuários cujo nome começa com "Ana"
SELECT * FROM usuarios WHERE nome LIKE 'Ana%';

-- Buscar e-mails de um domínio específico
SELECT * FROM usuarios WHERE email LIKE '%@empresa.com';
```

**Uso em QA:** validar se dados de texto foram gravados com o formato correto.

---

## Cenário completo — Investigação de bug

**Situação:** o sistema deveria enviar e-mail de confirmação para todos os pedidos concluídos, mas alguns clientes reclamaram que não receberam.

```sql
-- Passo 1: quantos pedidos foram concluídos?
SELECT COUNT(*) FROM pedidos WHERE status = 'concluido';

-- Passo 2: desses, quantos têm e-mail de confirmação registrado?
SELECT COUNT(*) FROM pedidos
WHERE status = 'concluido' AND email_confirmacao_enviado = 1;

-- Passo 3: quais pedidos NÃO tiveram e-mail enviado?
SELECT pedidos.id, clientes.nome, clientes.email
FROM pedidos
JOIN clientes ON pedidos.cliente_id = clientes.id
WHERE pedidos.status = 'concluido'
AND pedidos.email_confirmacao_enviado = 0;

-- Passo 4: algum desses clientes tem e-mail nulo?
SELECT pedidos.id, clientes.nome
FROM pedidos
JOIN clientes ON pedidos.cliente_id = clientes.id
WHERE pedidos.status = 'concluido'
AND clientes.email IS NULL;
```

**Conclusão:** com essas queries é possível identificar exatamente quais pedidos falharam e se o problema está nos dados (e-mail nulo) ou no processo de envio.

---

*Repositório de estudos — Camila Lopes | QA em formação*
