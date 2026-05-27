# Login Test Cases

Casos de teste para validação do fluxo de autenticação (login) do sistema.

---

## CT001 - Login com credenciais válidas

### Tipo
Funcional — Smoke Test

### Prioridade
Alta

### Objetivo
Validar que o login é realizado com sucesso ao inserir credenciais corretas.

### Pré-condição
Usuário cadastrado e ativo no sistema (ex: `camila@teste.com` / senha: `Senha@123`).

### Passos
1. Acessar a tela de login
2. Inserir e-mail válido cadastrado no sistema
3. Inserir senha correta
4. Clicar no botão "Login"

### Resultado esperado
- Usuário autenticado com sucesso
- Redirecionado para o dashboard
- Nome do usuário exibido no cabeçalho da página

### Status
- [ ] Não executado

---

## CT002 - Login com senha incorreta

### Tipo
Funcional

### Prioridade
Alta

### Objetivo
Validar que o sistema exibe mensagem de erro ao inserir senha incorreta.

### Pré-condição
Usuário cadastrado e ativo no sistema.

### Passos
1. Acessar a tela de login
2. Inserir e-mail válido cadastrado no sistema
3. Inserir senha incorreta (ex: `SenhaErrada1`)
4. Clicar no botão "Login"

### Resultado esperado
- Sistema não autentica o usuário
- Exibe mensagem: `"E-mail ou senha inválidos."`
- Usuário permanece na tela de login
- Campo de senha é limpo automaticamente

### Status
- [ ] Não executado

---

## CT003 - Login com e-mail não cadastrado

### Tipo
Funcional

### Prioridade
Alta

### Objetivo
Validar que o sistema rejeita tentativas de login com e-mail inexistente no sistema.

### Pré-condição
Usuário na tela de login.

### Passos
1. Acessar a tela de login
2. Inserir e-mail não cadastrado no sistema (ex: `naoexiste@teste.com`)
3. Inserir qualquer senha
4. Clicar no botão "Login"

### Resultado esperado
- Sistema não autentica o usuário
- Exibe mensagem genérica: `"E-mail ou senha inválidos."` (mesma mensagem do CT002, sem revelar que o e-mail não existe)
- Usuário permanece na tela de login

> **Nota:** A mensagem de erro deve ser idêntica à do CT002. Mensagens distintas (como "usuário não encontrado") permitem que atacantes descubram quais e-mails estão cadastrados.

### Status
- [ ] Não executado

---

## CT004 - Login com e-mail em formato inválido

### Tipo
Funcional

### Prioridade
Média

### Objetivo
Validar que o sistema rejeita e-mails com formato inválido antes de submeter o formulário.

### Pré-condição
Usuário na tela de login.

### Passos
1. Acessar a tela de login
2. Inserir e-mail com formato inválido no campo de e-mail (exemplos abaixo)
3. Inserir qualquer senha
4. Clicar no botão "Login"

**Entradas para testar:**
| Entrada | Motivo |
|---|---|
| `camila` | Sem @ e sem domínio |
| `camila@` | Sem domínio |
| `@teste.com` | Sem nome de usuário |
| `camila@teste` | Sem extensão de domínio |

### Resultado esperado
- Sistema bloqueia a submissão do formulário
- Exibe mensagem: `"Insira um endereço de e-mail válido."`
- Usuário permanece na tela de login

### Status
- [ ] Não executado

---

## CT005 - Login com campo e-mail vazio

### Tipo
Funcional

### Prioridade
Alta

### Objetivo
Validar que o sistema bloqueia a tentativa de login quando o campo e-mail está vazio.

### Pré-condição
Usuário na tela de login.

### Passos
1. Acessar a tela de login
2. Deixar o campo "E-mail" em branco
3. Inserir senha válida
4. Clicar no botão "Login"

### Resultado esperado
- Sistema bloqueia a submissão do formulário
- Exibe mensagem: `"O campo e-mail é obrigatório."` abaixo do campo de e-mail
- Formulário não é submetido

### Status
- [ ] Não executado

---

## CT006 - Login com campo senha vazio

### Tipo
Funcional

### Prioridade
Alta

### Objetivo
Validar que o sistema bloqueia a tentativa de login quando o campo senha está vazio.

### Pré-condição
Usuário na tela de login.

### Passos
1. Acessar a tela de login
2. Inserir e-mail válido
3. Deixar o campo "Senha" em branco
4. Clicar no botão "Login"

### Resultado esperado
- Sistema bloqueia a submissão do formulário
- Exibe mensagem: `"O campo senha é obrigatório."` abaixo do campo de senha
- Formulário não é submetido

### Status
- [ ] Não executado

---

## CT007 - Login sem preencher nenhum campo

### Tipo
Funcional

### Prioridade
Alta

### Objetivo
Validar que o sistema bloqueia a tentativa de login quando nenhum campo está preenchido.

### Pré-condição
Usuário na tela de login.

### Passos
1. Acessar a tela de login
2. Não preencher nenhum campo
3. Clicar no botão "Login"

### Resultado esperado
- Sistema bloqueia a submissão do formulário
- Exibe simultaneamente as mensagens: `"O campo e-mail é obrigatório."` e `"O campo senha é obrigatório."`
- Formulário não é submetido

### Status
- [ ] Não executado

---

## CT008 - Login com espaços antes ou depois das credenciais

### Tipo
Funcional — Edge Case

### Prioridade
Média

### Objetivo
Validar que o sistema ignora espaços acidentais inseridos antes ou depois das credenciais (trim).

### Pré-condição
Usuário cadastrado e ativo no sistema.

### Passos
1. Acessar a tela de login
2. Inserir o e-mail com espaço antes e/ou depois (ex: `" camila@teste.com "`)
3. Inserir senha correta
4. Clicar no botão "Login"

### Resultado esperado
- Sistema remove os espaços automaticamente e autentica o usuário com sucesso
- **OU** exibe mensagem de erro informando credenciais inválidas (comportamento deve ser documentado e consistente)

### Status
- [ ] Não executado

---

## CT009 - Login com usuário inativo ou bloqueado

### Tipo
Funcional

### Prioridade
Alta

### Objetivo
Validar que o sistema impede o login de usuários com conta inativa ou bloqueada.

### Pré-condição
Usuário cadastrado no sistema com status **inativo** ou **bloqueado**.

### Passos
1. Acessar a tela de login
2. Inserir e-mail de usuário inativo/bloqueado
3. Inserir senha correta
4. Clicar no botão "Login"

### Resultado esperado
- Sistema não autentica o usuário
- Exibe mensagem informando que a conta está inativa ou bloqueada (ex: `"Sua conta está desativada. Entre em contato com o suporte."`)
- Usuário permanece na tela de login

### Status
- [ ] Não executado

---

## CT010 - Bloqueio por excesso de tentativas de login (Brute Force)

### Tipo
Funcional — Segurança

### Prioridade
Alta

### Objetivo
Validar que o sistema bloqueia temporariamente o acesso após múltiplas tentativas de login com falha consecutivas.

### Pré-condição
Usuário cadastrado no sistema. Sistema configurado para bloquear após N tentativas (ex: 5).

### Passos
1. Acessar a tela de login
2. Inserir e-mail válido e senha incorreta
3. Clicar no botão "Login"
4. Repetir os passos 2 e 3 até atingir o limite de tentativas (ex: 5 vezes)

### Resultado esperado
- Após atingir o limite, o sistema bloqueia novas tentativas
- Exibe mensagem: `"Muitas tentativas. Tente novamente em X minutos."` ou similar
- O bloqueio deve persistir mesmo após recarregar a página

### Status
- [ ] Não executado

---

## Resumo de cobertura

| ID | Cenário | Tipo | Prioridade | Status |
|---|---|---|---|---|
| CT001 | Login com credenciais válidas | Smoke Test | Alta | Não executado |
| CT002 | Login com senha incorreta | Funcional | Alta | Não executado |
| CT003 | Login com e-mail não cadastrado | Funcional | Alta | Não executado |
| CT004 | Login com e-mail em formato inválido | Funcional | Média | Não executado |
| CT005 | Campo e-mail vazio | Funcional | Alta | Não executado |
| CT006 | Campo senha vazio | Funcional | Alta | Não executado |
| CT007 | Nenhum campo preenchido | Funcional | Alta | Não executado |
| CT008 | Espaços antes/depois das credenciais | Edge Case | Média | Não executado |
| CT009 | Usuário inativo ou bloqueado | Funcional | Alta | Não executado |
| CT010 | Bloqueio por excesso de tentativas | Segurança | Alta | Não executado |

---

> **Nota sobre CT005 original (senha abaixo do tamanho mínimo):** A validação de tamanho mínimo de senha pertence ao fluxo de **Cadastro** ou **Alteração de Senha**, não ao Login. No login, qualquer sequência de caracteres é uma tentativa de credencial — se não bater com a senha cadastrada, é coberto pelo CT002.

---

*Repositório de estudos — Camila Lopes | QA em formação*




