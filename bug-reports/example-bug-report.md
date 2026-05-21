# Bug Report — BUG-001

## Título
Sistema permite tentativa de login com campos obrigatórios vazios

## Tipo
Funcional

## Severidade
Média — não impede o uso do sistema, mas indica falha na validação de entrada

## Prioridade
Alta — campos obrigatórios sem validação comprometem a experiência e a segurança

## Ambiente
- Navegador: Google Chrome 124
- Sistema operacional: Windows 11
- Tela: /login

## Pré-condição
Usuário na tela de login, sem nenhum dado preenchido.

## Passos para reproduzir
1. Acessar a tela de login
2. Deixar os campos "Usuário" e "Senha" vazios
3. Clicar no botão "Login"

## Resultado esperado
Sistema bloqueia a tentativa e exibe mensagem informando que os campos são obrigatórios.

## Resultado obtido
Sistema tenta processar a autenticação sem validar os campos. 
Nenhuma mensagem de erro é exibida ao usuário.

## Evidências
[inserir print da tela]

## Observações
Testado também sem preencher apenas um dos campos — comportamento idêntico.


