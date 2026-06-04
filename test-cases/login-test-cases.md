# Login — Casos de Teste

Casos de teste para validação do fluxo de autenticação (login) do sistema.

**Sistema sob teste:** ServeRest — https://front.serverest.dev  
**Data de execução:** 04/06/2026  
**Ambiente:** Produção  
**Executado por:** Camila Lopes  

---

## CT001 - Login com credenciais válidas

### Tipo
Funcional — Smoke Test

### Prioridade
Alta

### Objetivo
Validar que o login é realizado com sucesso ao inserir credenciais corretas.

### Pré-condição
Usuário cadastrado e ativo no sistema.

### Dados de teste
| Campo | Valor |
|---|---|
| E-mail | fulano@qa.com |
| Senha | teste |

### Passos
1. Acessar `https://front.serverest.dev/login`
2. Inserir e-mail válido cadastrado no sistema
3. Inserir senha correta
4. Clicar no botão "Entrar"

### Resultado esperado
- Usuário autenticado com sucesso
- Redirecionado para o dashboard
- Nome do usuário exibido no cabeçalho da página

### Resultado obtido
- Login realizado com sucesso
- Redirecionado para o dashboard
- Nome "Fulano da Silva" exibido no cabeçalho ✅

### Evidência
> `evidencias/ct001-login-sucesso.png`

### Status
- [x] Executado

### Resultado
✅ **Aprovado**

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

### Dados de teste
| Campo | Valor |
|---|---|
| E-mail | fulano@qa.com |
| Senha | senhaerrada |

### Passos
1. Acessar a tela de login
2. Inserir e-mail válido
3. Inserir senha incorreta
4. Clicar no botão "Entrar"

### Resultado esperado
- Sistema não autentica o usuário
- Exibe mensagem: `"E-mail ou senha inválidos."`
- Usuário permanece na tela de login

### Resultado obtido
- Sistema não autenticou o usuário ✅
- Exibiu mensagem de erro ✅
- ⚠️ A mensagem aparece **cortada** na interface — exibe apenas `"E-mail e/ou senha"` sem completar o texto

### Evidência
> `evidencias/ct002-senha-incorreta.png`

### Bug vinculado
🐛 [BUG-002 — Mensagem de erro de login cortada na interface](../bug-reports/BUG-002-mensagem-cortada.md)

### Status
- [x] Executado

### Resultado
✅ **Aprovado com observação** — bug de layout registrado

---

## CT003 - Login com e-mail não cadastrado

### Tipo
Funcional

### Prioridade
Alta

### Objetivo
Validar que o sistema rejeita tentativas de login com e-mail inexistente.

### Dados de teste
| Campo | Valor |
|---|---|
| E-mail | naoexiste@teste.com |
| Senha | qualquercoisa |

### Passos
1. Acessar a tela de login
2. Inserir e-mail não cadastrado
3. Inserir qualquer senha
4. Clicar no botão "Entrar"

### Resultado esperado
- Sistema não autentica o usuário
- Exibe mensagem genérica idêntica ao CT002 (sem revelar que o e-mail não existe)

### Resultado obtido
- Sistema não autenticou ✅
- Exibiu a mesma mensagem do CT002 ✅ — não revela se o e-mail existe no sistema

### Evidência
> `evidencias/ct003-email-nao-cadastrado.png`

### Status
- [x] Executado

### Resultado
✅ **Aprovado**

---

## CT004 - Login com e-mail em formato inválido

### Tipo
Funcional

### Prioridade
Média

### Objetivo
Validar que o sistema rejeita e-mails fora do formato esperado.

### Dados de teste
| Entrada | Motivo |
|---|---|
| `camilasemarroba` | Sem @ e sem domínio |

### Passos
1. Acessar a tela de login
2. Inserir e-mail sem @ no campo de e-mail
3. Inserir qualquer senha
4. Clicar no botão "Entrar"

### Resultado esperado
- Sistema bloqueia a submissão
- Exibe mensagem de formato inválido

### Resultado obtido
- Sistema bloqueou a submissão ✅
- ⚠️ Mensagem exibida pelo **browser** (validação HTML nativa): `"Inclua um @ no endereço de e-mail. camilasemarroba está com um @ faltando."`
- Não é mensagem do ServeRest

### Evidência
> `evidencias/ct004-email-invalido.png`

### Status
- [x] Executado

### Resultado
✅ **Aprovado** (validação via browser, não via sistema)

---

## CT005 - Login com campo e-mail vazio

### Tipo
Funcional

### Prioridade
Alta

### Objetivo
Validar que o sistema bloqueia o login quando o campo e-mail está vazio.

### Passos
1. Acessar a tela de login
2. Deixar o campo e-mail em branco
3. Inserir senha válida
4. Clicar no botão "Entrar"

### Resultado esperado
- Sistema bloqueia a submissão
- Exibe mensagem de campo obrigatório

### Resultado obtido
- Sistema exibiu mensagem: `"Email não pode ficar em branco"` ✅
- Formulário não foi submetido ✅

### Evidência
> `evidencias/ct005-email-vazio.png`

### Status
- [x] Executado

### Resultado
✅ **Aprovado**

---

## CT006 - Login com campo senha vazio

### Tipo
Funcional

### Prioridade
Alta

### Objetivo
Validar que o sistema bloqueia o login quando o campo senha está vazio.

### Passos
1. Acessar a tela de login
2. Inserir e-mail válido
3. Deixar o campo senha em branco
4. Clicar no botão "Entrar"

### Resultado esperado
- Sistema bloqueia a submissão
- Exibe mensagem de campo obrigatório

### Resultado obtido
- Sistema exibiu mensagem: `"A senha não pode ficar em branco"` ✅
- Formulário não foi submetido ✅

### Evidência
> `evidencias/ct006-senha-vazia.png`

### Status
- [x] Executado

### Resultado
✅ **Aprovado**

---

## CT007 - Login sem preencher nenhum campo

### Tipo
Funcional

### Prioridade
Alta

### Objetivo
Validar que o sistema bloqueia o login quando nenhum campo está preenchido.

### Passos
1. Acessar a tela de login
2. Não preencher nenhum campo
3. Clicar no botão "Entrar"

### Resultado esperado
- Sistema exibe as duas mensagens simultaneamente

### Resultado obtido
- Sistema exibiu simultaneamente: ✅
  - `"Email não pode ficar em branco"`
  - `"A senha não pode ficar em branco"`

### Evidência
> `evidencias/ct007-campos-vazios.png`

### Status
- [x] Executado

### Resultado
✅ **Aprovado**

---

## CT008 - Login com espaços antes ou depois das credenciais

### Tipo
Funcional — Edge Case

### Prioridade
Média

### Objetivo
Validar que o sistema ignora espaços acidentais nas credenciais (trim).

### Dados de teste
| Campo | Valor |
|---|---|
| E-mail | ` fulano@qa.com` (com espaço antes) |
| Senha | teste |

### Passos
1. Acessar a tela de login
2. Inserir e-mail com espaço antes
3. Inserir senha correta
4. Clicar no botão "Entrar"

### Resultado esperado
- Sistema remove os espaços e autentica com sucesso

### Resultado obtido
- Sistema removeu o espaço automaticamente e autenticou com sucesso ✅

### Evidência
> `evidencias/ct008-espacos.png`

### Status
- [x] Executado

### Resultado
✅ **Aprovado**

---

## CT009 - Login com usuário inativo ou bloqueado

### Tipo
Funcional

### Prioridade
Alta

### Status
- [x] Executado

### Resultado
⏭️ **Não aplicável** — o ServeRest não possui conceito de usuário inativo ou bloqueado. Cenário válido para sistemas com gestão de status de usuário.

---

## CT010 - Bloqueio por excesso de tentativas (Brute Force)

### Tipo
Funcional — Segurança

### Prioridade
Alta

### Status
- [x] Executado

### Resultado
⏭️ **Não aplicável** — o ServeRest não possui proteção contra múltiplas tentativas de login. Cenário válido para sistemas com política de segurança de acesso.

---

## Resumo de execução

| ID | Cenário | Prioridade | Resultado |
|---|---|---|---|
| CT001 | Login com credenciais válidas | Alta | ✅ Aprovado |
| CT002 | Login com senha incorreta | Alta | ✅ Aprovado ⚠️ bug de layout |
| CT003 | E-mail não cadastrado | Alta | ✅ Aprovado |
| CT004 | E-mail com formato inválido | Média | ✅ Aprovado (browser) |
| CT005 | Campo e-mail vazio | Alta | ✅ Aprovado |
| CT006 | Campo senha vazio | Alta | ✅ Aprovado |
| CT007 | Nenhum campo preenchido | Alta | ✅ Aprovado |
| CT008 | Espaços nas credenciais | Média | ✅ Aprovado |
| CT009 | Usuário inativo/bloqueado | Alta | ⏭️ Não aplicável |
| CT010 | Brute force | Alta | ⏭️ Não aplicável |

**Total:** 10 casos | ✅ 8 aprovados | ⏭️ 2 não aplicáveis | 🐛 1 bug registrado

---

*Repositório de estudos — Camila Lopes | QA em formação*