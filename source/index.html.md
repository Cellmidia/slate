---
title: Cellmidia API Reference

language_tabs:
  - shell
  - php

toc_footers:
  - <a href='#'>Cellmidia Developers Team</a>

includes:
  - errors

search: true
---

# Visão Geral

Bem vindo a Cellmidia API! Você pode usar nossa API para acessar os endpoints da Cellmidia API, que você poderá usar
para obter informações sobre o envio de SMS.

Nossas APIs são baseadas em métodos HTTP, o que torna fácil escrever aplicações e integrar nossos serviços. Você poderá
usar qualquer cliente HTTP em qualquer linguagem de programação ou até mesmo no seu navegador para interagir com a nossa
API.

Vamos sempre por exemplos de uso usando o Shell e PHP! Você pode ver os exemplos nas guias mais a direita.

Base URL padrão
----------------

A base url padrão da Cellmidia API é: `http://api.smsapp.com.br`

NOTA: Nessa fase as chamadas de API podem serem feitas sem uso do HTTPS, mas por razões de segurança na próxima
atualização o uso de SSL será obrigatória.

Content-Type
------------

Nossa API só aceita entradas do tipo `application/json`. Todas as solitações `POST` os argumentos devem ser passados
como json explicitanto o  `Content-Type` definido como `application/json`.

API Request
-----------

    A Cellmidia API expõe uma lista de serviços REST para várias ações para a gestão da sua conta, envios de SMS e
    relatórios.

    Todas as requisições devem ser feitas em: `http://api.smsapp.com.br/v1`

API Response
-----------

 Todas as APIs da Cellmidia retornam uma resposta em formato JSON. A API pode retornar um dos seguintes códigos de status HTTP.

     código | descrição
     ------ | ---------
     200 | Request has been executed
     201 | Resource created
     202 | Resource changed
     204 | Resource deleted
     400 | A parameter is missing or is invalid
     401 | Authentication failed
     404 | Resource cannot be found
     405 | HTTP method not allowed
     409 | Conflict
     500 | Server error



# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

