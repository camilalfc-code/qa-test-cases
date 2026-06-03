# BUG-001 — Sistema aceita senha fraca no cadastro

## Informações gerais

| Campo | Valor |
|---|---|
| **ID** | BUG-001 |
| **Título** | Sistema aceita senha fraca no cadastro de usuário |
| **Módulo** | Cadastro de Usuário |
| **Reportado por** | Camila Lopes |
| **Data** | 03/06/2026 |
| **Ambiente** | Produção — https://front.serverest.dev |
| **Severidade** | Alta |
| **Prioridade** | Alta |
| **Status** | Aberto |

---

## Descrição

O sistema permite o cadastro de novos usuários com senhas extremamente fracas, sem aplicar nenhuma validação de complexidade. Senhas como `123456` são aceitas sem qualquer restrição, o que representa uma vulnerabilidade de segurança.

---

## Passos para reproduzir

1. Acessar `https://front.serverest.dev/cadastrarusuarios`
2. Preencher o campo **Nome** com qualquer valor (ex: `Camila QA`)
3. Preencher o campo **E-mail** com um e-mail válido não cadastrado (ex: `teste.fraco@teste.com`)
4. Preencher o campo **Senha** com `123456`
5. Clicar no botão **"Cadastrar"**

---

## Resultado obtido

✅ Cadastro realizado com sucesso.
Sistema aceitou a senha `123456` sem exibir nenhum aviso ou bloqueio.
Usuário foi redirecionado para o dashboard normalmente.

---

## Resultado esperado

❌ Sistema deveria bloquear o cadastro e exibir mensagem informando os requisitos mínimos de senha, por exemplo:

> *"A senha deve ter no mínimo 8 caracteres, incluindo letras e números."*

---

## Evidência

> `evidencias/ct006-senha-fraca.png`

---

## Impacto

- Usuários podem criar contas com senhas facilmente descobertas
- Risco de ataques de força bruta e acesso não autorizado
- Não conformidade com boas práticas de segurança (OWASP)

---

## Caso de teste relacionado

[CT006 — Cadastro com senha fraca](../test-cases/cadastro-test-cases.md#ct006---cadastro-com-senha-fraca)

---

*Repositório de estudos — Camila Lopes | QA em formação*