# Campanhas

Visão Geral
-----------

Recursos de campanha é a representação de uma campanha que poderá ser enviada pelo Cliente.


## Campanha

Para se criar uma campanha deve-se ultilizar o seguinte endpoint:

    `POST /campaign`

Para se editar uma campanha deve-se ultilizar o seguinte endpoint:

    `PUT /campaign/ID`
    
Para se listar todas as campanhas deve-se ultilizar o seguinte endpoint:

    `GET /campaign`
 

### Criando campanha

```http
POST /campaign HTTP/1.1
Accept: application/json
User-Agent: Http/2.2
Host: HOST

{
    "title": "This is a title",
    "content": "This is a content",
    "sender": "Something",
    "status": "created"
}
```

> A solicitação acima retorna a seguinte resposta:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "content": "This is a content",
  "createAt": "2016-06-17T18:21:23+00:00",
  "id": 1,
  "lastModifiedAt": "2016-06-17T18:21:23+00:00",
  "title": "This is a title",
  "sender": "Something",
  "status": "created
}
```
> Se a campanha estiver incorreta o retorno será o seguinte:

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
    "error": "The content \"invalid\" needs to be between 10 and 150 chars.",
    "code": 409
}
```

**CAMPANHA PARA PARAMENTROS INCORRETOS**

Argumento | Mensagem
--------- | -----------
content | The content "invalid" needs to be between 10 and 150 chars.
title | The title "invalid" needs to be between 4 and 60 chars.
sender | The sender "invalid" needs to be between 3 and 10 chars.
status | Invalid status.


O Recurso de Campanha é composto pelos seguintes atributos

Atributo | Descrição
-------- | ---------
+ id | Representa uma ID
+ createdAt  | Representa a data de criação
+ modifieddAt  | Representa a data de modificação
+ owner | Representa uma account
+ content | Representa um texto de mensagem
+ title | Representa o nome da campanha
+ sender | Representa o remetente
+ status | Representa o status


 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
content |  Sim | String entre 10-150 caracteres
title | Sim | String entre 4-60 caracteres
sender | Sim | String entre 4-10 caracteres
status | Sim | Constante 

* Response

Atributo | Descrição
-------- | ---------
+ id | Novo ID
+ createdAt  | DateTime atual
+ modifieddAt  | DateTime atual
+ content | A mesma usada na solicitação
+ title | A mesma usada na solicitação
+ sender | A mesma usada na solicitação
+ status | A mesma usada na solicitação


### Listando todas as campanhas

```http
GET /campaign HTTP/1.1
Accept: application/json
User-Agent: Http/2.2
Host: HOST

{
    
}
```

> Se houver campanhas o retorno será o seguinte:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "count": 2,
    "items": [
        {
          "content": "This is a content",
          "createAt": "2016-06-17T18:21:23+00:00",
          "id": 1,
          "lastModifiedAt": "2016-06-17T18:21:23+00:00",
          "title": "This is a title",
          "sender": "Something",
          "status": "created
        },
        {
          "content": "This is a content",
          "createAt": "2016-06-17T18:21:23+00:00",
          "id": 2,
          "lastModifiedAt": "2016-06-17T18:21:23+00:00",
          "title": "This is a title",
          "sender": "Something",
          "status": "created
        }
    ]
}
```

> Se não houver campanhas o retorno será o seguinte:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "error": "You don't have any Campaign yet.",
    "code": 404
}
```

**PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
ID_Account | Sim | O ID irá ser gerado de acordo com a Account que está logada

* Response

Atributo | Descrição
-------- | ---------
+ count | Contador
+ items  | Array de campanhas 

### Editando campanha

```http
PUT /campaign/ID HTTP/1.1
Accept: application/json
User-Agent: Http/2.2
Host: HOST

{
    "title": "This is a modified",
    "content": "This is a modified",
    "sender": "Modified",
}
```

> A solicitação acima retorna a seguinte resposta:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "content": "This is a modified",
  "createAt": "2016-06-17T18:21:23+00:00",
  "id": 1,
  "lastModifiedAt": "2016-06-17T18:21:23+00:00",
  "title": "This is a modified",
  "sender": "Modified",
  "status": "created
}
```
> Se a campanha estiver incorreta o retorno será o seguinte:

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
    "error": "The content \"invalid\" needs to be between 10 and 150 chars.",
    "code": 409
}
```

**CAMPANHA PARA PARAMENTROS INCORRETOS**

Argumento | Mensagem
--------- | -----------
content | The content "invalid" needs to be between 10 and 150 chars.
title | The title "invalid" needs to be between 4 and 60 chars.
sender | The sender "invalid" needs to be between 3 and 10 chars.



 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
content |  Não | String entre 10-150 caracteres
title | Não | String entre 4-60 caracteres
sender | Não | String entre 4-10 caracteres

* Response

Atributo | Descrição
-------- | ---------
+ id | A mesma gerada na criação
+ createdAt  | A mesma gerada na criação
+ modifieddAt  | A mesma gerada na criação
+ content | A mesma usada na solicitação
+ title | A mesma usada na solicitação
+ sender | A mesma usada na solicitação
+ status | A mesma gerada na criação
