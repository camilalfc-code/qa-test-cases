# Checklist e Classificação de Bug Reports

Guia de referência rápida para garantir qualidade no registro de bugs e classificação correta de severidade e prioridade.

---

## Checklist — antes de abrir um bug

Use este checklist antes de registrar qualquer bug no JIRA para garantir que o relatório está completo e útil.

- [ ] Consegui reproduzir o bug pelo menos **3 vezes**?
- [ ] Testei em **mais de um navegador ou dispositivo**?
- [ ] O bug acontece em **homologação, produção ou ambos**?
- [ ] Tenho uma **evidência** (print, vídeo ou log)?
- [ ] O **título** descreve claramente o que falhou e onde?
- [ ] Os **passos para reproduzir** são suficientes para o dev repetir sem me perguntar nada?
- [ ] Preenchi **resultado esperado** E **resultado obtido** separadamente?
- [ ] Classifiquei corretamente **severidade** e **prioridade**?
- [ ] Verifiquei se esse bug **já foi registrado antes** (duplicata)?

---

## Guia de classificação — Severidade

A severidade mede o **impacto técnico** do bug no sistema.

| Severidade | Critério | Exemplos |
|---|---|---|
| **Crítica** | Sistema inoperante ou perda de dados. Sem alternativa. | Não é possível fazer login; dados do usuário são apagados ao salvar |
| **Alta** | Funcionalidade principal quebrada. Há workaround mas é inadequado. | Pagamento não processa; relatório exporta dados errados |
| **Média** | Funcionalidade afetada mas há alternativa viável. | Filtro de busca retorna resultado incorreto; campo não valida formato |
| **Baixa** | Problema visual, textual ou de usabilidade. Não afeta fluxo. | Botão com cor errada; erro de digitação em label; ícone desalinhado |

---

## Guia de classificação — Prioridade

A prioridade mede a **urgência de correção**, considerando impacto no negócio.

| Prioridade | Critério |
|---|---|
| **Urgente** | Precisa ser corrigido hoje. Impacta operação ou clientes diretamente. |
| **Alta** | Deve entrar na próxima sprint. Afeta fluxo principal. |
| **Média** | Pode aguardar priorização pelo time. Não bloqueia entregas. |
| **Baixa** | Entra no backlog. Corrigir quando houver oportunidade. |

---

## Combinações comuns de severidade × prioridade

| Situação | Severidade | Prioridade | Por quê |
|---|---|---|---|
| Login completamente quebrado em produção | Crítica | Urgente | Impacta todos os usuários agora |
| Bug em funcionalidade legada que ninguém usa | Alta | Baixa | Grave tecnicamente, mas sem impacto real no negócio |
| Erro visual na home em Black Friday | Baixa | Alta | Tecnicamente pequeno, mas o momento é crítico para o negócio |
| Campo obrigatório sem validação | Média | Alta | Não quebra o sistema, mas compromete integridade dos dados |
| Texto errado em página de erro 404 | Baixa | Baixa | Não afeta nenhuma funcionalidade |

---

## Tipos de bug mais comuns em testes funcionais

**Validação de entrada**
Campos que aceitam valores inválidos, vazios ou fora do formato esperado.
Exemplo: campo de e-mail aceita "teste@" sem domínio.

**Regra de negócio**
O sistema não aplica uma regra definida nos requisitos.
Exemplo: desconto de 10% para clientes Premium não é calculado.

**Comportamento inesperado após ação**
O sistema reage de forma diferente do esperado após uma interação.
Exemplo: item removido do carrinho reaparece após atualizar a página.

**Inconsistência de dados**
Dados exibidos na interface não correspondem ao que está no banco.
Exemplo: saldo exibido na tela é diferente do valor no banco de dados.

**Compatibilidade**
Bug que aparece em um ambiente específico (browser, dispositivo, resolução).
Exemplo: botão sobreposto ao rodapé apenas em mobile.

**Problema de fluxo**
Usuário consegue acessar uma etapa sem ter completado a anterior.
Exemplo: é possível finalizar a compra sem adicionar endereço de entrega.

---

## Títulos bons vs. ruins

| ❌ Título fraco | ✅ Título claro |
|---|---|
| "Erro na tela de login" | "[BUG] Login não realizado com credenciais válidas — usuário permanece na tela" |
| "Botão não funciona" | "[BUG] Botão 'Finalizar compra' não responde ao clique no Safari iOS" |
| "Problema no cadastro" | "[BUG] Campo CPF aceita letras e caracteres especiais sem exibir erro" |
| "Página quebrada" | "[BUG] Página de perfil retorna erro 500 ao acessar sem foto cadastrada" |

---

*Repositório de estudos — Camila Lopes | QA em formação*
