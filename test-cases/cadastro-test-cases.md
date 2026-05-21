# Cadastro de Usuário — Test Cases

Casos de teste para validação do fluxo de cadastro de novo usuário no sistema.

---

## CT001 - Cadastro com dados válidos

### Tipo
Funcional — Smoke Test

### Objetivo
Validar que o cadastro é realizado com sucesso ao preencher todos os campos corretamente.

### Pré-condição
Usuário não cadastrado no sistema.
Acesso à tela de cadastro.

### Passos
1. Acessar a tela de cadastro
2. Preencher nome completo: "Maria Silva"
3. Preencher e-mail válido: "maria@teste.com"
4. Preencher senha válida: "Senha@123"
5. Confirmar senha: "Senha@123"
6. Clicar no botão "Cadastrar"

### Resultado esperado
Cadastro realizado com sucesso.
Usuário redirecionado para a tela de login ou dashboard.
Mensagem de confirmação exibida.

### Status
- [ ] Não executado

---

## CT002 - Cadastro com e-mail já existente

### Tipo
Funcional

### Objetivo
Validar que o sistema impede cadastro com e-mail já registrado.

### Pré-condição
Usuário com e-mail "maria@teste.com" já cadastrado no sistema.

### Passos
1. Acessar a tela de cadastro
2. Preencher nome: "João Silva"
3. Preencher e-mail já existente: "maria@teste.com"
4. Preencher senha válida
5. Confirmar senha
6. Clicar no botão "Cadastrar"

### Resultado esperado
Sistema bloqueia o cadastro e exibe mensagem: "Este e-mail já está cadastrado."
Nenhum novo usuário é criado no banco de dados.

### Status
- [ ] Não executado

---

## CT003 - Cadastro com e-mail em formato inválido

### Tipo
Funcional

### Objetivo
Validar que o sistema rejeita e-mails fora do formato esperado.

### Pré-condição
Acesso à tela de cadastro.

### Passos
1. Acessar a tela de cadastro
2. Preencher nome válido
3. Inserir e-mail inválido: "mariatesте.com" (sem @)
4. Preencher senha válida
5. Confirmar senha
6. Clicar no botão "Cadastrar"

### Resultado esperado
Sistema exibe mensagem de erro: "Insira um e-mail válido."
Formulário não é submetido.

### Status
- [ ] Não executado

---

## CT004 - Cadastro com senhas diferentes na confirmação

### Tipo
Funcional

### Objetivo
Validar que o sistema rejeita o cadastro quando senha e confirmação de senha não coincidem.

### Pré-condição
Acesso à tela de cadastro.

### Passos
1. Acessar a tela de cadastro
2. Preencher nome e e-mail válidos
3. Inserir senha: "Senha@123"
4. Inserir confirmação diferente: "Senha@456"
5. Clicar no botão "Cadastrar"

### Resultado esperado
Sistema exibe mensagem: "As senhas não coincidem."
Formulário não é submetido.

### Status
- [ ] Não executado

---

## CT005 - Cadastro com campo obrigatório vazio

### Tipo
Funcional

### Objetivo
Validar que o sistema bloqueia o cadastro quando algum campo obrigatório não está preenchido.

### Pré-condição
Acesso à tela de cadastro.

### Passos
1. Acessar a tela de cadastro
2. Preencher e-mail e senha válidos
3. Deixar o campo "Nome" em branco
4. Clicar no botão "Cadastrar"

### Resultado esperado
Sistema bloqueia o envio e exibe mensagem indicando que o campo nome é obrigatório.

### Status
- [ ] Não executado

---

## CT006 - Cadastro com senha fraca

### Tipo
Funcional

### Objetivo
Validar que o sistema rejeita senhas que não atendem aos critérios mínimos de segurança.

### Pré-condição
Sistema exige senha com mínimo 8 caracteres, letra maiúscula e caractere especial.
Acesso à tela de cadastro.

### Passos
1. Acessar a tela de cadastro
2. Preencher nome e e-mail válidos
3. Inserir senha fraca: "123456"
4. Confirmar a mesma senha
5. Clicar no botão "Cadastrar"

### Resultado esperado
Sistema bloqueia o cadastro e exibe mensagem informando os requisitos mínimos de senha.

### Status
- [ ] Não executado

---

## Resumo de cobertura

| ID | Cenário | Tipo | Status |
|---|---|---|---|
| CT001 | Cadastro com dados válidos | Smoke Test | Não executado |
| CT002 | E-mail já cadastrado | Funcional | Não executado |
| CT003 | E-mail com formato inválido | Funcional | Não executado |
| CT004 | Senhas diferentes na confirmação | Funcional | Não executado |
| CT005 | Campo obrigatório vazio | Funcional | Não executado |
| CT006 | Senha fraca | Funcional | Não executado |

---

*Repositório de estudos — Camila Lopes | QA em formação*
