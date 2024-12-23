# Postman

# Documetação

# Configuração do ambiente
Para acessar as APIs protegidas, é necessário obter um token JWT. Isso é feito por meio de uma requisição POST para o endpoint de login/autenticação.
A url para obtenção do token JWT é https://serverest.dev/login
O Método usado para a execução é POST
No Headers deve conter o parâmetro:
Content-Type: application/json

O body da requisição deve ser
{
  "email": "joao.silva@email.com",
  "password": "senha123"
}

a resposta para o suceso da autenticação deve ser:
{
  "message": "Login realizado com sucesso",
  "authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}

# passo-a-passo para a execução dos testes
1) cadastrar um usuário
2) Realizar a autenticação do usuário cadastrado via requisição no postman
3) realizar a busca do usuário cadastrado via requisição no postman
4) Validar os detalhes do usuário cadastrado via requisição no postman
5) Alterar os dados do usuário cadastrado via requisição no postman
6) Realizar o delete do usuário cadastrado via requisição do postman
