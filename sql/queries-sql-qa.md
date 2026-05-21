# Casos de Uso — SQL em Testes de Software
Cenários práticos de como um analista de QA usa SQL no dia a dia para validar dados e investigar problemas.


## Caso 1 — Validar cadastro de usuário

### Objetivo
Situação: após preencher e submeter o formulário de cadastro na interface, verificar se os dados foram gravados corretamente.


### Passos
Buscar o usuário pelo e-mail informado no cadastro

SELECT id, nome, email, status, data_criacao

FROM usuarios

WHERE email = 'camila@teste.com';


### O que validar:
Nome gravado sem caracteres estranhos

E-mail em letras minúsculas (ou conforme regra do sistema)

Status = 'ativo' (ou o valor esperado para novo cadastro)

Data de criação corresponde ao momento do teste




