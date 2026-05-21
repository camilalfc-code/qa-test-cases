# Fluxo de QA com JIRA — Guia Prático

Documentação do fluxo de trabalho de um analista de QA usando JIRA em ambiente ágil.

---

## 1. O que é o JIRA no contexto de QA

O JIRA é a ferramenta mais usada por equipes de tecnologia para gerenciar tarefas, bugs e testes. Para o QA, ele serve para:

- Criar e acompanhar **tickets de teste**
- Registrar **bugs** com todas as informações necessárias para o dev reproduzir
- Acompanhar o **status de cada defeito** até a resolução
- Organizar o trabalho dentro do **Scrum Board**

---

## 2. Tipos de tickets em QA

| Tipo | Quando criar | Exemplo |
|---|---|---|
| **Bug** | Comportamento inesperado encontrado | Login não funciona com senha correta |
| **Task** | Tarefa de teste planejada | Executar casos de teste do módulo de pagamento |
| **Story** | Funcionalidade a ser testada | Como usuário, quero resetar minha senha |
| **Sub-task** | Parte menor de uma task maior | Testar fluxo de reset por e-mail |

---

## 3. Fluxo de status de um bug no JIRA

```
ABERTO → EM ANÁLISE → EM DESENVOLVIMENTO → PRONTO PARA TESTE → RETESTE → FECHADO
                                                                    ↓
                                                              (se falhou)
                                                            REABERTO → EM DESENVOLVIMENTO
```

### Descrição de cada status

**Aberto (Open)**
Bug registrado pelo QA. Ainda não foi analisado pelo time de desenvolvimento.

**Em análise (In Analysis)**
O dev está avaliando a causa do problema.

**Em desenvolvimento (In Progress)**
Correção em andamento.

**Pronto para teste (Ready for Test)**
Dev sinalizou que corrigiu. QA deve executar o reteste.

**Reteste (In Review / Testing)**
QA está verificando se o bug foi realmente corrigido.

**Fechado (Done / Closed)**
Bug confirmado como corrigido após reteste com sucesso.

**Reaberto (Reopened)**
Reteste falhou — o bug ainda existe ou a correção gerou um novo problema.

---

## 4. Como registrar um bug no JIRA

Um bom registro de bug tem informações suficientes para que o desenvolvedor consiga reproduzir o problema **sem precisar perguntar nada**.

### Campos obrigatórios

| Campo | O que preencher |
|---|---|
| **Título** | Resumo claro do problema — o que falhou e onde |
| **Ambiente** | Onde foi encontrado: produção, homologação, browser, dispositivo |
| **Passos para reproduzir** | Sequência exata de ações para chegar ao erro |
| **Resultado esperado** | O que deveria acontecer |
| **Resultado obtido** | O que aconteceu de fato |
| **Evidência** | Print, vídeo ou log do erro |
| **Severidade** | O quanto impacta o sistema |
| **Prioridade** | Urgência de correção |

---

## 5. Severidade vs. Prioridade

Muitos confundem esses dois campos. São conceitos diferentes.

### Severidade — impacto técnico no sistema

| Nível | Descrição | Exemplo |
|---|---|---|
| **Crítico** | Sistema inoperante, sem workaround | Não é possível fazer login de jeito nenhum |
| **Alto** | Funcionalidade principal quebrada | Pagamento não processa |
| **Médio** | Funcionalidade afetada mas há alternativa | Filtro de busca retorna resultado errado, mas busca manual funciona |
| **Baixo** | Problema visual ou de usabilidade | Botão com cor errada, texto com erro de digitação |

### Prioridade — urgência de correção

| Nível | Descrição |
|---|---|
| **Urgente** | Precisa ser corrigido hoje |
| **Alto** | Próxima sprint |
| **Médio** | Pode aguardar priorização |
| **Baixo** | Backlog, corrigir quando possível |

> Um bug pode ter **severidade alta e prioridade baixa** — por exemplo, uma funcionalidade legada que quase ninguém usa mas que está completamente quebrada.

---

## 6. Scrum Board — organização visual das tarefas

O Scrum Board no JIRA organiza os tickets em colunas visuais, permitindo que o time acompanhe o progresso da sprint.

```
┌──────────────┬──────────────┬──────────────┬──────────────┐
│   TO DO      │ IN PROGRESS  │   TESTING    │    DONE      │
├──────────────┼──────────────┼──────────────┼──────────────┤
│ QA-101       │ QA-98        │ QA-95        │ QA-90        │
│ Testar login │ Corrigir bug │ Reteste pag. │ Fluxo cadastro│
│              │ do carrinho  │              │ ✅ aprovado  │
│ QA-102       │              │              │              │
│ Testar perfil│              │              │ QA-91        │
│              │              │              │ Busca filtros │
│              │              │              │ ✅ aprovado  │
└──────────────┴──────────────┴──────────────┴──────────────┘
```

### Como o QA usa o Scrum Board

- Move tickets de **To Do → In Progress** quando começa a executar os testes
- Move para **Testing** quando um bug volta do dev para reteste
- Move para **Done** após confirmar que está funcionando
- **Reabre** o ticket se o reteste falhar

---

## 7. Tipos de teste e quando aplicar no ciclo

### Smoke Test
Verificação rápida das funcionalidades principais logo após um deploy.
Objetivo: confirmar que o sistema está operacional antes de testes mais detalhados.

**Exemplo:** após deploy do módulo de pagamento, testar apenas se é possível completar uma compra do início ao fim.

### Teste de Regressão
Verificação de que funcionalidades que já funcionavam continuam funcionando após uma mudança no código.
Objetivo: garantir que a correção de um bug não quebrou outra coisa.

**Exemplo:** após correção do bug de login, executar todos os casos de teste do módulo de autenticação para garantir que nada foi quebrado.

### Reteste
Verificação específica de um bug que foi corrigido.
Objetivo: confirmar que aquele defeito em particular foi resolvido.

**Exemplo:** o bug QA-98 "botão de checkout desaparece no mobile" foi corrigido — testar exatamente esse comportamento novamente.

---

## 8. Ciclo completo — exemplo prático

**Situação:** durante os testes do módulo de carrinho de compras, o QA encontra um bug.

**Passo 1 — Identificar e reproduzir**
Reproduzir o bug pelo menos 3 vezes para confirmar que não foi um erro pontual.

**Passo 2 — Registrar no JIRA**
```
Título: [BUG] Item removido do carrinho volta a aparecer ao atualizar a página

Ambiente: Homologação | Chrome 124 | Desktop

Passos para reproduzir:
1. Acessar o site e fazer login
2. Adicionar qualquer produto ao carrinho
3. Acessar o carrinho
4. Clicar em "Remover" no produto
5. Confirmar que o produto foi removido
6. Pressionar F5 para atualizar a página

Resultado esperado:
Carrinho permanece vazio após atualização.

Resultado obtido:
O produto removido reaparece no carrinho após atualizar a página.

Evidência: [print em anexo]

Severidade: Alta
Prioridade: Alta
```

**Passo 3 — Acompanhar no board**
Mover o ticket conforme o status: Aberto → Em análise → Em desenvolvimento.

**Passo 4 — Reteste**
Quando o dev marcar como "Pronto para Teste", executar novamente os passos do bug.

**Passo 5 — Fechar ou Reabrir**
- Correção funcionou → **Fechar** o ticket
- Problema persiste → **Reabrir** com comentário explicando o que foi encontrado no reteste

---

*Repositório de estudos — Camila Lopes | QA em formação*
