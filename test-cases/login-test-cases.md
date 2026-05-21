# Login Test Cases

Casos de teste para validação do fluxo de autenticação (login) do sistema.

---

## CT001 - Login com credenciais válidas

### Tipo
Funcional — Smoke Test

### Objetivo
Validar que o login é realizado com sucesso ao inserir credenciais corretas.

### Pré-condição
Usuário cadastrado e ativo no sistema.

### Passos
1. Acessar a tela de login
2. Inserir e-mail válido cadastrado no sistema
3. Inserir senha correta
4. Clicar no botão "Login"

### Resultado esperado
Usuário autenticado com sucesso e redirecionado para a página inicial (dashboard).

### Status
- [ ] Não executado

---

## CT002 - Login com senha incorreta

### Tipo
Funcional

### Objetivo
Validar que o sistema exibe mensagem de erro ao inserir senha incorreta.

### Pré-condição
Usuário cadastrado e ativo no sistema.

### Passos
1. Acessar a tela de login
2. Inserir e-mail válido cadastrado no sistema
3. Inserir senha incorreta
4. Clicar no botão "Login"

### Resultado esperado
Sistema não autentica o usuário e exibe mensagem: "E-mail ou senha inválidos."
Usuário permanece na tela de login.

### Status
- [ ] Não executado

---

## CT003 - Login com campo usuário vazio

### Tipo
Funcional

### Objetivo
Validar que o sistema bloqueia a tentativa de login quando o campo usuário está vazio.

### Pré-condição
Usuário na tela de login, nenhum campo preenchido.

### Passos
1. Acessar a tela de login
2. Deixar o campo "Usuário / E-mail" em branco
3. Inserir senha válida
4. Clicar no botão "Login"

### Resultado esperado
Sistema bloqueia a tentativa e exibe mensagem informando que o campo usuário é obrigatório.
Formulário não é submetido.

### Status
- [ ] Não executado

---

## CT004 - Login com campo senha vazio

### Tipo
Funcional

### Objetivo
Validar que o sistema bloqueia a tentativa de login quando o campo senha está vazio.

### Pré-condição
Usuário na tela de login, nenhum campo preenchido.

### Passos
1. Acessar a tela de login
2. Inserir e-mail válido
3. Deixar o campo "Senha" em branco
4. Clicar no botão "Login"

### Resultado esperado
Sistema bloqueia a tentativa e exibe mensagem informando que o campo senha é obrigatório.
Formulário não é submetido.

### Status
- [ ] Não executado

---

## CT005 - Login com senha abaixo do tamanho mínimo

### Tipo
Funcional

### Objetivo
Validar que o sistema rejeita senhas com menos caracteres do que o mínimo exigido.

### Pré-condição
Sistema exige senha de no mínimo 8 caracteres.
Usuário na tela de login.

### Passos
1. Acessar a tela de login
2. Inserir e-mail válido
3. Inserir senha com menos de 8 caracteres (ex: "abc123")
4. Clicar no botão "Login"

### Resultado esperado
Sistema bloqueia a tentativa e exibe mensagem informando o tamanho mínimo da senha.
Formulário não é submetido.

### Status
- [ ] Não executado

---

## CT006 - Login sem preencher nenhum campo

### Tipo
Funcional

### Objetivo
Validar que o sistema bloqueia a tentativa de login quando nenhum campo está preenchido.

### Pré-condição
Usuário na tela de login, todos os campos vazios.

### Passos
1. Acessar a tela de login
2. Não preencher nenhum campo
3. Clicar no botão "Login"

### Resultado esperado
Sistema bloqueia a tentativa e exibe mensagens de campo obrigatório para usuário e senha simultaneamente.
Formulário não é submetido.

### Status
- [ ] Não executado

---

## Resumo de cobertura

| ID | Cenário | Tipo | Status |
|---|---|---|---|
| CT001 | Login válido | Smoke Test | Não executado |
| CT002 | Senha incorreta | Funcional | Não executado |
| CT003 | Campo usuário vazio | Funcional | Não executado |
| CT004 | Campo senha vazio | Funcional | Não executado |
| CT005 | Senha abaixo do mínimo | Funcional | Não executado |
| CT006 | Nenhum campo preenchido | Funcional | Não executado |

---

*Repositório de estudos — Camila Lopes | QA em formação*


