# Login Test Cases

## CT001 - Login válido

### Objetivo
Validar login com credenciais válidas.

### Pré-condição
Usuário cadastrado no sistema.

### Passos
1. Acessar tela de login
2. Inserir usuário válido
3. Inserir senha válida
4. Clicar em Login

### Resultado esperado
Usuário acessa o sistema com sucesso.

---

## CT002 - Senha inválida

### Objetivo
Validar mensagem de erro ao inserir senha inválida.

### Resultado esperado
Sistema exibe mensagem de erro.

---

## CT003 - Campo usuário vazio

### Objetivo
Validar comportamento do sistema ao deixar o campo usuário vazio.

### Passos
1. Acessar tela de login
2. Deixar campo usuário em branco
3. Inserir senha válida
4. Clicar em Login

### Resultado esperado
Sistema exibe mensagem informando que o usuário é obrigatório.

---

## CT004 - Campo senha vazio

### Objetivo
Validar comportamento do sistema ao deixar o campo senha vazio.

### Passos
1. Acessar tela de login
2. Inserir usuário válido
3. Deixar campo senha em branco
4. Clicar em Login

### Resultado esperado
Sistema exibe mensagem informando que a senha é obrigatória.

