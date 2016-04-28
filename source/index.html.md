---
title: Cellmidia API - Documentação de referência

lang: pt-BR

language_tabs:
  - http
  - php

includes:
    - authorization
    - http_status_code

toc_footers:
  - <a href='#'>Cellmidia Developers Team</a>
---

# Visão Geral

Bem vindo a documentaçao da Cellmidia API! Esta é a API utilizada por nossa interface Web.

Nossas APIs são baseadas em métodos HTTP, o que torna fácil escrever aplicações e integrar nossos serviços. Você poderá
usar qualquer cliente HTTP em qualquer linguagem de programação ou até mesmo no seu navegador para interagir com a nossa
API.

# Enviando requisições

Quando você for escrever seu próprio cliente para nossa API, por favor tenha em mente o seguinte:

* Sempre defina o cabeçalho **User-Agent**. Este cabeçalho não é obrigatório por agora, mas ele será no futuro próximo.
  Por exemplo seu cliente de API é chamado de "MyClient", e a versão atual dele seja 1.0.0, seria boa prática usar isso
  como valor para este cabeçalho `MyClient/1.0.0`
* Sempre defina o cabeçalho **Accept** para `application/json`

<aside class="notice">
    Se você não definir o cabeçalho <b>Content-Type</b> e <b>Accept</b> você estará automaticamente recuperando nosso formato JSON.
</aside>

Qualquer biblioteca existente deve dar conta disso para você.

API Endpoint
----------------

A API endpoint da Cellmidia API é: `http://api.smsapp.com.br`

NOTA: Nessa fase as chamadas de API podem serem feitas sem uso do HTTPS, mas na próxima
atualização o uso de SSL será obrigatória.

Encoding
---------

Nossa API usa o *character encoding* em **UTF-8**. As requisições podem incluir um
**Content-Type** como `application/json; charset=utf-8`

Padrões de Data e Hora
----------------------

Todos os timestamps estão formatados de acordo com a [ISO-8601](https://en.wikipedia.org/wiki/ISO_8601).

Content-Type
------------

Nossa API só aceita entradas do tipo `application/json`. Todas as solitações `POST` os argumentos devem ser passados
como json explicitanto o  `Content-Type` definido como `application/json`.

Todas requisições `GET` e `DELETE` devem ter seus argumentos passados como `QUERY STRING`

API Request
-----------

A Cellmidia API expõe uma lista de serviços REST que permitem realizar as mais variadas tarefas tais como, enviar SMS,
cadastrar um conta, entre outras.

Todas as requisições devem apontar no seguinte endpoit: `http://api.smsapp.com.br/v1`

API Response
-----------

A maioria dos pedidos de requisição retornam um resposta em formato **JSON** e um **HTTP STATUS**.

Uma lista de retornos HTTP e seus respectivos códigos podem ser exploradas [nesta seção](#http-status-code).
