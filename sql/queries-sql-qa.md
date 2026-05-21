-- Buscar o usuário pelo e-mail informado no cadastro
SELECT id, nome, email, status, data_criacao
FROM usuarios
WHERE email = 'camila@teste.com';
