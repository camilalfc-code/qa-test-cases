# Casos de Uso — SQL em Testes de Software
Cenários práticos de como um analista de QA usa SQL no dia a dia para validar dados e investigar problemas.


## Caso 1 — Validar cadastro de usuário

### Objetivo
Situação: após preencher e submeter o formulário de cadastro na interface, verificar se os dados foram gravados corretamente.


### Passos
1.Buscar o usuário pelo e-mail informado no cadastro
2.SELECT id, nome, email, status, data_criacao
3.FROM usuarios
4.WHERE email = 'camila@teste.com';

### O que validar:
1.Nome gravado sem caracteres estranhos
2.E-mail em letras minúsculas (ou conforme regra do sistema)
3.Status = 'ativo' (ou o valor esperado para novo cadastro)
4.Data de criação corresponde ao momento do teste



