# Autorização e Autenticação

Visão Geral
-----------

Nossa API faz uso do padrão JWT ou [JSON Web Tokens](https://tools.ietf.org/html/rfc7519).

Recursos de autorização é a representação de uma autorização concedida ao usuário para realizar qualquer ação.

**Somente** você pode conceder estas autorizações através de um token.

Esta API permite você autenticar seus usários do seu Cliente enviando solicitações de login para sua própria API.

Auth Endpoint
---------------

O endpoint para autenticação e authorização é: `http://id.cellmidia.com.br`

#Autenticação

##Autorizações

Existem duas formas de realizar autorização:

* Credenciais
* Token

Ambas estratégias devem ser feitas no seguinte endpoint:

    `POST /authentication`

### Autorização usando credenciais

```http
POST /authentication HTTP/1.1
Accept: application/json
User-Agent: Http/2.2
Host: id.cellmidia.com.br

{
    "username": "youraccount@cellmidia.com.br",
    "password": "YourGreatPassword",
    "type": "credentials"
}
```

> A solicitação acima retorna a seguinte resposta:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJqdGkiOiI1NmZlOGI3ZjVhNDgxIiwiaXNzIjoiYXBpLmNlbGxtaWRpYS5kZXYiLCJhdWQiOiJodHRwOlwvXC9pZC5jZWxsbWlkaWEuZGV2XC8iLCJ1c2VyIjp7InVzZXJuYW1lIjoiZG9taW5nb3NAY2VsbG1pZGlhLmNvbS5iciJ9LCJleHAiOjE0NTk1MjYwMzF9.lCMFHlPvkTP3DHmpthQQNYXNk8QECPePL2wJW5Mt1IY",
    "renew_token":"e7032dd7c38240bbdc4a79452aa07192784be680"
}
```
> Se as credenciais estiverem incorretas  o retorno será o seguinte:

```http
HTTP/1.1 401 Unauthorized
Content-Type: application/json

{
    "error":"Invalid credentials.",
    "code":401
}
```

O Recurso de autorização é composto pelos seguintes atributos:

Atributo | Descrição
-------- | ---------
+ access_token | Representa um JWT
+ renew_token  | Representa sua chave de validação do access_token


 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
username | Sim | Seu usuário sempre no formato `usuario@dominio.com; ≤1023 bytes
password | Sim | Sua senha; ≤1023 bytes
type | Sim | `credentials`

### Autorização usando o Token de Renovação

```http
POST /authentication HTTP/1.1
Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJqdGkiOiI1NmZlOGI3ZjVhNDgxIiwiaXNzIjoiYXBpLmNlbGxtaWRpYS5kZXYiLCJhdWQiOiJodHRwOlwvXC9pZC5jZWxsbWlkaWEuZGV2XC8iLCJ1c2VyIjp7InVzZXJuYW1lIjoiZG9taW5nb3NAY2VsbG1pZGlhLmNvbS5iciJ9LCJleHAiOjE0NTk1MjYwMzF9.lCMFHlPvkTP3DHmpthQQNYXNk8QECPePL2wJW5Mt1IY
Accept: application/json
User-Agent: Http/2.2
Host id.cellmidia.com.br

{
    "type": "token"
}
```
> Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "access_token":"eyJ0eXAiOiJKV1MiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJzYjphdXRoOnN0YWdpbmciLCJqdGkiOiI1NTY0ZDhlYTU5MDYyIiwidXNlciI6eyJpZCI6MiwidXNlcm5hbWUiOiJhZG1pbkBzb2NpYWxiYXNlLmxvY2FsIiwiZW1haWwiOiJhZG1pbkBzb2NpYWxiYXNlLmNvbS5iciIsIm5hbWUiOiJBZG1pbiJ9LCJuZXR3b3JrIjp7ImlkIjoxLCJuYW1lIjoiU29jaWFsQmFzZSBWMyIsInJlc291cmNlIjoiZGV2LXNvY2lhbGJhc2UiLCJhcG4iOiJodHRwOlwvXC9sb2NhbGhvc3Q6OTAwNSJ9LCJleHAiOjE0MzI2NzYwOTB9.9ijI-XZ8GfHE69NFcMUs_kHtR2pv0jel5U3Yha0OK-M",
    "renew_token":"e7032dd7c38240bbdc4a79452aa07192784be680"
}
```

As vezes será necessário renovar o token (Long term session).

 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
type | Sim | `renew_token` obtido na solicitação usando credenciais.


* Response

Atributo | Descrição
-------- | ---------
+ access_token | Um novo Token JWT
+ renew_token  | a mesma usada na solicitação
