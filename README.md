
# Atividade P2 - Desenvolvimento das Funcionalidades

Nesta atividade, você deverá implementar as seguintes funcionalidades:

## 1. Login

O usuário deve realizar login utilizando o endpoint abaixo:

```
curl -X POST https://go-wash-api.onrender.com/api/login \
-H "Content-Type: application/json" \
-d '{
  "email": "carlosr.m.fernandes@gmail.com",
  "password": "123456",
  "user_type_id": 1
}'
```

Após o login, será retornado um token JWT. Esse token deverá ser utilizado nas próximas requisições, no cabeçalho `Authorization`.

## 2. Tela de Listagem de Endereços

Após o login, o usuário será redirecionado para a tela de listagem de endereços, utilizando o seguinte endpoint:

```
curl -X GET https://go-wash-api.onrender.com/api/auth/address \
-H "Authorization: Bearer <JWT_TOKEN>"
```

Nessa tela, deve ser exibida uma tabela com todos os endereços cadastrados, contendo as seguintes informações:

| Título     | CEP       | Endereço                                    | Número | Ações               |
|------------|-----------|---------------------------------------------|--------|---------------------|
| Minha Casa | 03730000  | Rua Brazópolis, Jardim Jaú (Zona Leste)     | 8A     | Atualizar / Deletar |

A tela deve conter um botão **"Cadastrar Endereço"**, que levará o usuário para a tela de cadastro.

## 3. Cadastro de Endereço

Para cadastrar um novo endereço, utilize o seguinte endpoint:

```
curl -X POST https://go-wash-api.onrender.com/api/auth/address \
-H "Content-Type: application/json" \
-H "Authorization: Bearer <JWT_TOKEN>" \
-d '{
  "title": "Minha Casa",
  "cep": "03730000",
  "address": "Rua Brazópolis, Jardim Jaú (Zona Leste)",
  "number": "8A",
  "complement": ""
}'
```

Após o cadastro, o usuário deverá ser redirecionado novamente para a tela de listagem, onde o novo endereço aparecerá na tabela.

## 4. Atualização de Endereço


Na listagem, cada linha da tabela deverá conter um botão **"Atualizar"**, que abrirá uma tela ou modal para edição dos dados. Para atualizar, utilize:

1 - Busca o endereço pelo id, e apresenta os dados nos inputs

```
curl --location 'https://go-wash-api.onrender.com/api/auth/address/{id}' \
-H "Authorization: Bearer <JWT_TOKEN>" \
--data ''
```
2 - Ao clicar no botão **"Atualizar"** dever fazer a atualização 
```
curl -X POST https://go-wash-api.onrender.com/api/auth/address/{id} \
-H "Content-Type: application/json" \
-H "Authorization: Bearer <JWT_TOKEN>" \
-d '{
  "title": "Minha Casa",
  "cep": "03730000",
  "address": "Rua Brazópolis, Jardim Jaú (Zona Leste)",
  "number": "8A",
  "complement": ""
}'
```

## 5. Deleção de Endereço

Na mesma tabela, haverá também um botão **"Deletar"**. Para deletar um endereço, utilize:

```
curl -X DELETE https://go-wash-api.onrender.com/api/auth/address/{id} \
-H "Authorization: Bearer <JWT_TOKEN>"
```

## Objetivo

Praticar autenticação, consumo de API REST e manipulação de dados dinâmicos na interface.
