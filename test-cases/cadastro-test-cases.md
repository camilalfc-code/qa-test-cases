# Cadastro de Usuário — Casos de Teste

Casos de teste para validação do fluxo de cadastro de novo usuário no sistema.

**Sistema sob teste:** ServeRest — https://front.serverest.dev  
**Data de execução:** 03/06/2026  
**Ambiente:** Produção  
**Executado por:** Camila Lopes  

---

## CT001 - Cadastro com dados válidos

### Tipo
Funcional — Smoke Test

### Prioridade
Alta

### Objetivo
Validar que o cadastro é realizado com sucesso ao preencher todos os campos corretamente.

### Pré-condição
Usuário não cadastrado no sistema.
Acesso à tela de cadastro.

### Dados de teste
| Campo | Valor |
|---|---|
| Nome | Camila QA |
| E-mail | camila.qa.2026@teste.com |
| Senha | teste123 |

### Passos
1. Acessar `https://front.serverest.dev/cadastrarusuarios`
2. Preencher nome completo
3. Preencher e-mail válido não cadastrado
4. Preencher senha
5. Clicar no botão "Cadastrar"

### Resultado esperado
Cadastro realizado com sucesso.
Usuário redirecionado para o dashboard.
Mensagem de confirmação exibida.

### Resultado obtido
Cadastro realizado com sucesso.
Usuário redirecionado para o dashboard com lista de produtos.
⚠️ Nenhuma mensagem de confirmação foi exibida — o sistema redirecionou diretamente.

### Evidência
> `evidencias/ct001-cadastro-sucesso.png`

### Status
- [x] Executado

### Resultado
✅ **Aprovado com observação**

---

## CT002 - Cadastro com e-mail já existente

### Tipo
Funcional

### Prioridade
Alta

### Objetivo
Validar que o sistema impede cadastro com e-mail já registrado.

### Pré-condição
Usuário com e-mail `camila.qa.2026@teste.com` já cadastrado no sistema (CT001 executado).

### Dados de teste
| Campo | Valor |
|---|---|
| Nome | Outro Nome |
| E-mail | camila.qa.2026@teste.com |
| Senha | teste123 |

### Passos
1. Acessar a tela de cadastro
2. Preencher nome diferente
3. Preencher e-mail já cadastrado
4. Preencher senha
5. Clicar no botão "Cadastrar"

### Resultado esperado
Sistema bloqueia o cadastro e exibe mensagem de e-mail duplicado.

### Resultado obtido
Sistema exibiu mensagem: **"Este email já está sendo usado"**
Cadastro bloqueado corretamente.

### Evidência
> `evidencias/ct002-email-duplicado.png`

### Status
- [x] Executado

### Resultado
✅ **Aprovado**

---

## CT003 - Cadastro com e-mail em formato inválido

### Tipo
Funcional

### Prioridade
Média

### Objetivo
Validar que o sistema rejeita e-mails fora do formato esperado.

### Dados de teste
| Campo | Valor |
|---|---|
| Nome | Camila QA |
| E-mail | camilateste.com (sem @) |
| Senha | teste123 |

### Passos
1. Acessar a tela de cadastro
2. Inserir e-mail sem @ no campo e-mail
3. Preencher nome e senha válidos
4. Clicar no botão "Cadastrar"

### Resultado esperado
Sistema bloqueia o envio e exibe mensagem de formato inválido.

### Resultado obtido
Sistema bloqueou o envio.
⚠️ A mensagem exibida foi gerada pelo próprio navegador (validação HTML nativa): **"Inclua um @ no endereço de e-mail. camilateste.com está com um @ faltando."**
Não é uma mensagem do ServeRest — é uma validação do browser.

### Evidência
> `evidencias/ct003-email-invalido.png`

### Status
- [x] Executado

### Resultado
✅ **Aprovado** (validação via browser, não via sistema)

---

## CT004 - Cadastro com senhas diferentes na confirmação

### Tipo
Funcional

### Prioridade
Média

### Objetivo
Validar que o sistema rejeita o cadastro quando senha e confirmação de senha não coincidem.

### Passos
1. Acessar a tela de cadastro
2. Preencher nome e e-mail válidos
3. Inserir senhas diferentes nos campos de senha e confirmação

### Resultado esperado
Sistema exibe mensagem: "As senhas não coincidem."

### Resultado obtido
⏭️ **Não aplicável** — o ServeRest não possui campo de confirmação de senha no formulário de cadastro.

### Status
- [x] Executado

### Resultado
⏭️ **Não aplicável ao sistema**

---

## CT005 - Cadastro com campo obrigatório vazio

### Tipo
Funcional

### Prioridade
Alta

### Objetivo
Validar que o sistema bloqueia o cadastro quando campo obrigatório não está preenchido.

### Dados de teste
| Campo | Valor |
|---|---|
| Nome | (vazio) |
| E-mail | teste@teste.com |
| Senha | teste123 |

### Passos
1. Acessar a tela de cadastro
2. Deixar o campo "Nome" em branco
3. Preencher e-mail e senha válidos
4. Clicar no botão "Cadastrar"

### Resultado esperado
Sistema bloqueia o envio e exibe mensagem indicando campo obrigatório.

### Resultado obtido
Sistema exibiu mensagem: **"Nome não pode ficar em branco"**
Cadastro bloqueado corretamente.

### Evidência
> `evidencias/ct005-campo-vazio.png`

### Status
- [x] Executado

### Resultado
✅ **Aprovado**

---

## CT006 - Cadastro com senha fraca

### Tipo
Funcional — Segurança

### Prioridade
Alta

### Objetivo
Validar que o sistema rejeita senhas que não atendem aos critérios mínimos de segurança.

### Dados de teste
| Campo | Valor |
|---|---|
| Nome | Camila QA |
| E-mail | teste.fraco@teste.com |
| Senha | 123456 |

### Passos
1. Acessar a tela de cadastro
2. Preencher nome e e-mail válidos
3. Inserir senha fraca: `123456`
4. Clicar no botão "Cadastrar"

### Resultado esperado
Sistema bloqueia o cadastro e exibe mensagem informando os requisitos mínimos de senha.

### Resultado obtido
❌ Sistema **aceitou** a senha fraca `123456` e realizou o cadastro com sucesso.
Nenhuma validação de força de senha foi aplicada.

### Evidência
> `evidencias/ct006-senha-fraca.png`

### Bug vinculado
🐛 [BUG-001 — Sistema aceita senha fraca no cadastro](../bug-reports/BUG-001-senha-fraca.md)

### Status
- [x] Executado

### Resultado
❌ **Reprovado — Bug encontrado**

---

## Resumo de execução

| ID | Cenário | Prioridade | Resultado |
|---|---|---|---|
| CT001 | Cadastro com dados válidos | Alta | ✅ Aprovado com observação |
| CT002 | E-mail já cadastrado | Alta | ✅ Aprovado |
| CT003 | E-mail com formato inválido | Média | ✅ Aprovado (browser) |
| CT004 | Senhas diferentes na confirmação | Média | ⏭️ Não aplicável |
| CT005 | Campo obrigatório vazio | Alta | ✅ Aprovado |
| CT006 | Senha fraca aceita | Alta | ❌ Reprovado |

**Total:** 6 casos | ✅ 4 aprovados | ❌ 1 reprovado | ⏭️ 1 não aplicável

---

*Repositório de estudos — Camila Lopes | QA em formação*