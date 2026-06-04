# BUG-002 — Mensagem de erro de login cortada na interface

## Informações gerais

| Campo | Valor |
|---|---|
| **ID** | BUG-002 |
| **Título** | Mensagem de erro de login aparece cortada na interface |
| **Módulo** | Login / Autenticação |
| **Reportado por** | Camila Lopes |
| **Data** | 04/06/2026 |
| **Ambiente** | Produção — https://front.serverest.dev |
| **Severidade** | Baixa |
| **Prioridade** | Baixa |
| **Status** | Aberto |

---

## Descrição

Ao tentar fazer login com credenciais inválidas, a mensagem de erro exibida aparece truncada na interface. O texto `"E-mail e/ou senha inválidos"` é cortado, exibindo apenas `"E-mail e/ou senha"`, o que pode confundir o usuário sobre o motivo do erro.

---

## Passos para reproduzir

1. Acessar `https://front.serverest.dev/login`
2. Inserir e-mail válido: `fulano@qa.com`
3. Inserir senha incorreta: `senhaerrada`
4. Clicar no botão **"Entrar"**
5. Observar a mensagem de erro exibida

---

## Resultado obtido

A mensagem exibida aparece cortada: **`"E-mail e/ou senha"`**

O texto completo `"inválidos"` não é exibido ao usuário.

---

## Resultado esperado

A mensagem completa deveria ser exibida: **`"E-mail e/ou senha inválidos"`**

---

## Evidência

> `evidencias/ct002-senha-incorreta.png`

---

## Impacto

- Usuário pode não entender completamente o motivo do erro
- Problema de usabilidade e experiência do usuário (UX)
- Baixo impacto funcional — o bloqueio do login ocorre corretamente

---

## Caso de teste relacionado

[CT002 — Login com senha incorreta](../test-cases/login-test-cases.md#ct002---login-com-senha-incorreta)

---

*Repositório de estudos — Camila Lopes | QA em formação*