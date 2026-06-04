# 🧪 casos-de-teste-qa

<div align="center">

![QA Badge](https://img.shields.io/badge/QA-em%20formação-blueviolet?style=for-the-badge)
![Status](https://img.shields.io/badge/status-em%20andamento-yellow?style=for-the-badge)
![GitHub commits](https://img.shields.io/github/commit-activity/m/camilalfc-code/casos-de-teste-qa?style=for-the-badge&color=green)

**Repositório de estudos práticos em Quality Assurance**
Documentação, casos de teste executados, bug reports reais e consultas SQL organizados por módulo.

[📋 Casos de Teste](#-casos-de-teste) • [🐛 Bug Reports](#-bug-reports) • [🗄️ SQL](#️-sql) • [📌 JIRA](#-jira)

</div>

---

## 👩‍💻 Sobre

Olá! Sou **Camila Lopes**, funcionária pública em transição de carreira para QA, formanda em Análise e Desenvolvimento de Sistemas (ADS).

Este repositório reúne minha evolução prática em Quality Assurance — cada pasta representa uma competência desenvolvida para atuar como QA Júnior, com casos de teste **executados** contra o sistema real [ServeRest](https://front.serverest.dev).

---

## 📁 Estrutura do Repositório

```
casos-de-teste-qa/
│
├── 📂 casos de teste/              # Casos de teste manuais executados
│   ├── login-test-cases.md         # Suite completa — fluxo de autenticação
│   └── cadastro-test-cases.md      # Suite completa — fluxo de cadastro
│
├── 📂 relatórios de erros/         # Bug reports com evidências e severidade
│   ├── BUG-001-senha-fraca.md      # Sistema aceita senha fraca no cadastro
│   ├── BUG-002-mensagem-cortada.md # Mensagem de erro de login cortada na UI
│   └── checklist-bug-report.md     # Guia de classificação e checklist
│
├── 📂 SQL/                         # Consultas SQL para validação de dados
│   ├── queries-sql-qa.md           # Queries organizadas por tipo
│   └── Casos-sql-qa.md             # Cenários reais de uso de SQL em QA
│
├── 📂 JIRA/                        # Fluxo de trabalho e modelos para JIRA
│   ├── fluxo-qa-jira.md            # Fluxo completo de QA no JIRA
│   └── modelos-bug-report.md       # Modelos de registro de bug preenchidos
│
└── README.md
```

---

## 📋 Casos de Teste

Casos de teste escritos e **executados** com estrutura completa:
**pré-condição → passos → resultado esperado → resultado obtido → status**

| Suite | Cenários | Executados | Resultado |
|---|---|---|---|
| Login / Autenticação | 10 casos | 10 | ✅ 8 aprovados · ⏭️ 2 não aplicáveis |
| Cadastro de Usuário | 6 casos | 6 | ✅ 4 aprovados · ❌ 1 reprovado · ⏭️ 1 não aplicável |

**Técnicas aplicadas:**
- Partição de equivalência
- Análise de valor limite
- Fluxo alternativo e de exceção
- Edge cases

---

## 🐛 Bug Reports

Bugs reais encontrados durante a execução dos testes no ServeRest:

| ID | Título | Severidade | Status |
|---|---|---|---|
| [BUG-001](./relatórios%20de%20erros/BUG-001-senha-fraca.md) | Sistema aceita senha fraca no cadastro | Alta | Aberto |
| [BUG-002](./relatórios%20de%20erros/BUG-002-mensagem-cortada.md) | Mensagem de erro de login cortada na interface | Baixa | Aberto |

Bug reports estruturados com:
- Título objetivo e rastreável
- Passos para reprodução
- Resultado obtido vs. resultado esperado
- Severidade e prioridade
- Impacto e rastreabilidade com o caso de teste

---

## 🗄️ SQL

Consultas SQL para **validação de dados em banco**:

- Validação de registros criados via interface
- Verificação de integridade referencial
- Consultas para suporte a bug reports
- Queries de auditoria e rastreabilidade

---

## 📌 JIRA

Fluxo completo de QA com JIRA em ambiente ágil:

- Tipos de tickets: Bug, Task, Story, Sub-task
- Workflow: `Aberto → Em análise → Em desenvolvimento → Pronto para teste → Fechado`
- Modelos de bug report preenchidos com exemplos reais
- Guia de severidade vs. prioridade

---

## 🛠️ Tecnologias e Ferramentas

<div>

![Markdown](https://img.shields.io/badge/Markdown-000000?style=flat-square&logo=markdown&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)
![Jira](https://img.shields.io/badge/Jira-0052CC?style=flat-square&logo=jira&logoColor=white)
![MySQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=mysql&logoColor=white)

</div>

---

## 📈 Roadmap de Estudos

- [x] Fundamentos de casos de teste
- [x] Execução de testes e registro de resultados reais
- [x] Bug reports estruturados com bugs reais
- [x] SQL para QA
- [x] Jira — gestão de bugs e fluxo ágil
- [x] Git e GitHub
- [x] Automação E2E com Cypress
- [ ] Testes de API com Postman
- [ ] CTFL — ISTQB (certificação)

---

## 📂 Outros Repositórios

| Repositório | Descrição |
|---|---|
| [meu-projeto-cypress](https://github.com/camilalfc-code/meu-projeto-cypress) | Automação E2E com Cypress — 6 testes de login e cadastro |

---

## 📬 Contato

<div>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Camila%20Lopes-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/camila-lopes-qa)
[![GitHub](https://img.shields.io/badge/GitHub-camilalfc--code-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/camilalfc-code)

</div>

---

<div align="center">
  <sub>Feito com dedicação por Camila Lopes · QA em formação · 2026</sub>
</div>