# Autorização e Autenticação

Visão Geral
-----------
    Expomos aqui nossa API para Auntenticação e Autorização. É um serviço de AUTH Serveer que permite qualquer cliente
    consumir a Cellmidia API.

Base URL Padrão
---------------

    A base url padrão para autenticação e authorização é: `http://id.cellmidia.com.br`

    Nota: Nas próximas atualizações o uso desta API será somente via HTTPs.

#Autenticação

##Autorizações

    `POST /authentication`

### Autorização usando credenciais

    Recursos de autorização é a representação de uma autorização concedida ao usuário. **Somente** você pode conceder
    estas autorizações através de um **Autorização ao Portador**.

    O Recurso de autorização é composto pelos seguintes atributos:

    + access_token
    + renew_token

    Onde o *access_token* representa um [JSON Web Token](http://tools.ietf.org/html/draft-ietf-oauth-json-web-token-19),
    ou JWT.

    + Parâmetros
        + `username` (obrigatório, string) seu usuário
        + `password` (obrigatório, string) sua senha
        + `type` (obrigatório, string)  `credentials` ou `token`