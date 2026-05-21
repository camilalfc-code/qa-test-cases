# Modelos de Bug Report — Exemplos Preenchidos

Modelos práticos de registro de bug no JIRA, com exemplos reais de diferentes tipos de defeito.

---

## Modelo base

```
Título: [BUG] {descrição curta do problema — o que e onde}

Ambiente:
- Versão do sistema / build: 
- Navegador / dispositivo: 
- Sistema operacional: 
- URL / tela: 

Passos para reproduzir:
1. 
2. 
3. 

Resultado esperado:
{o que deveria acontecer}

Resultado obtido:
{o que aconteceu de fato}

Evidência:
{print / vídeo / log}

Severidade: Crítica / Alta / Média / Baixa
Prioridade: Urgente / Alta / Média / Baixa
```

---

## Exemplo 1 — Bug de autenticação (Severidade: Crítica)

```
Título: [BUG] Login não realizado com credenciais válidas — usuário fica na tela de login

Ambiente:
- Build: v2.4.1
- Navegador: Chrome 124 e Firefox 126 (reproduzível em ambos)
- Sistema operacional: Windows 11
- URL: https://app.exemplo.com/login

Passos para reproduzir:
1. Acessar a tela de login
2. Inserir e-mail cadastrado: teste@exemplo.com
3. Inserir senha correta: ********
4. Clicar em "Entrar"

Resultado esperado:
Usuário é autenticado e redirecionado para o dashboard.

Resultado obtido:
A tela de login recarrega sem mensagem de erro. 
O usuário não é autenticado e permanece na mesma tela.

Evidência: [screenshot anexado]

Severidade: Crítica (funcionalidade principal inoperante)
Prioridade: Urgente
```

---

## Exemplo 2 — Bug de validação de formulário (Severidade: Média)

```
Título: [BUG] Campo de e-mail aceita formato inválido no cadastro

Ambiente:
- Build: v2.4.1
- Navegador: Chrome 124
- Sistema operacional: macOS Ventura
- URL: https://app.exemplo.com/cadastro

Passos para reproduzir:
1. Acessar a tela de cadastro
2. Preencher o campo "E-mail" com o valor: "teste@"
3. Preencher os demais campos com dados válidos
4. Clicar em "Criar conta"

Resultado esperado:
Exibir mensagem de erro: "Por favor, insira um e-mail válido."
O formulário não deve ser submetido.

Resultado obtido:
O formulário é submetido com sucesso.
O cadastro é criado com o e-mail inválido "teste@" no banco de dados.

Evidência: [screenshot do cadastro criado]

Severidade: Média (validação falha mas sistema não fica inoperante)
Prioridade: Alta (dados inconsistentes no banco podem causar problemas futuros)
```

---

## Exemplo 3 — Bug visual / UI (Severidade: Baixa)

```
Título: [BUG] Botão "Confirmar pedido" sobreposto ao rodapé em telas mobile

Ambiente:
- Build: v2.4.1
- Dispositivo: iPhone 13 (375px de largura)
- Navegador: Safari iOS 17
- URL: https://app.exemplo.com/checkout

Passos para reproduzir:
1. Acessar o site pelo celular (ou redimensionar navegador para 375px)
2. Adicionar um produto ao carrinho
3. Avançar até a tela de checkout
4. Rolar a página até o final

Resultado esperado:
Botão "Confirmar pedido" visível e clicável acima do rodapé.

Resultado obtido:
Botão fica parcialmente sobreposto pelo rodapé, dificultando o clique.
Em algumas tentativas o clique não é registrado.

Evidência: [screenshot mobile anexado]

Severidade: Baixa (não impede a funcionalidade, mas prejudica a usabilidade)
Prioridade: Média (afeta experiência de usuários mobile)

Observação: testado também em Android Chrome — mesmo comportamento.
```

---

## Exemplo 4 — Bug de regra de negócio (Severidade: Alta)

```
Título: [BUG] Desconto de 10% não aplicado para clientes da categoria Premium

Ambiente:
- Build: v2.4.1
- Navegador: Chrome 124
- Sistema operacional: Windows 11
- URL: https://app.exemplo.com/carrinho

Passos para reproduzir:
1. Fazer login com conta de cliente Premium (categoria visível no perfil)
2. Adicionar qualquer produto ao carrinho
3. Verificar o valor total no carrinho

Resultado esperado:
Desconto de 10% aplicado automaticamente para clientes Premium.
Valor com desconto exibido no resumo do pedido.

Resultado obtido:
Nenhum desconto é aplicado. O valor cheio é exibido.
Validado via SQL: SELECT desconto FROM pedidos WHERE cliente_id = 42 → retorna 0.

Evidência: [screenshot do carrinho + resultado da query SQL]

Severidade: Alta (regra de negócio crítica não está funcionando)
Prioridade: Alta

Observação: testado com 3 contas Premium diferentes — problema reproduzível em todas.
```

---

## Dicas para um bom bug report

**Título objetivo:** deve responder "o que falhou" e "onde". Evite títulos vagos como "Erro na tela de pagamento".

**Passos precisos:** cada passo deve ser uma ação específica. O dev deve conseguir reproduzir sem adivinhar nada.

**Sempre incluir evidência:** print ou vídeo economiza tempo do dev e evita questionamentos.

**Separar severidade de prioridade:** são conceitos diferentes — veja o guia `fluxo-qa-jira.md`.

**Testar em mais de um ambiente:** se reproduzir em Chrome e Firefox, mencione os dois. Ajuda a identificar se é problema de compatibilidade.

---

*Repositório de estudos — Camila Lopes | QA em formação*
