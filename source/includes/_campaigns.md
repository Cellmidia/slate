# Ação

Visão Geral
-----------

Recursos de ação é a representação de uma ação que poderá ser enviada pelo Cliente.


## Ação

Para se criar uma ação deve-se ultilizar o seguinte endpoint:

    `POST /campaigns`

Para se editar uma ação deve-se ultilizar o seguinte endpoint:

    `PATCH /campaigns/ID`
    
Para se listar todas as ação deve-se ultilizar o seguinte endpoint:

    `GET /campaigns`
 
Para se listar todas as ação deve-se ultilizar o seguinte endpoint:

    `GET /campaigns/ID`
    
Para se deletar uma ação deve-se ultilizar o seguinte endpoint:

    `DELETE /campaigns/ID`
    
### Criando a ação

```http
POST /campaigns HTTP/1.1
Authorization: Bearer YourTokenComesHere
Accept: application/json
User-Agent: Http/2.2
Host: HOST

{
    "title": "This is a title",
    "content": "This is a content",
    "sender": "Something",
    "schedule": "2016-07-12 13:00"
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
  "status": "created",
  "schedule": "2016-07-12 13:00"
}
```
> Se a ação estiver incorreta o retorno será o seguinte:

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
    "error": "The content \"invalid\" needs to be between 10 and 150 chars.",
    "code": 409
}
```

**AÇÃO PARA PARAMENTROS INCORRETOS**

Argumento | Mensagem
--------- | -----------
content | The content "invalid" needs to be between 10 and 150 chars.
title | The title "invalid" needs to be between 4 and 60 chars.
sender | The sender "invalid" needs to be between 3 and 10 chars.


O Recurso de ação é composto pelos seguintes atributos

Atributo | Descrição
-------- | ---------
+ id | Representa uma ID
+ createdAt  | Representa a data de criação
+ modifieddAt  | Representa a data de modificação
+ content | Representa um texto de mensagem
+ title | Representa o nome da ação
+ sender | Representa o remetente da ação
+ status | Representa o status da ação
+ schedule | Representa o agendamento da açãp


 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
content |  Sim | String entre 10-150 caracteres
title | Sim | String entre 4-60 caracteres
sender | Sim | String entre 4-10 caracteres
schedule | Não | Data

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
+ schedule | A mesma usada na solicitação


### Editando a ação

```http
PATCH /campaigns/ID HTTP/1.1
Authorization: Bearer YourTokenComesHere
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
  "status": "created",
  "schedule": "2016-07-12 13:00"
}
```
> Se a ação estiver incorreta o retorno será o seguinte:

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
    "error": "The content \"invalid\" needs to be between 10 and 150 chars.",
    "code": 409
}
```

**AÇÃO PARA PARAMENTROS INCORRETOS**

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



### Listando todas as ações

```http
GET /campaigns HTTP/1.1 200 OK
Authorization: Bearer YourTokenComesHere
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
          "status": "created",
          "schedule": "2016-07-12 13:00",
          "statuses": [
              {
                "status": "created",
                "date": "2016-07-18T14:27:41+00:00"
              },
              {
                "status": "tested",
                "date": "2016-07-18T14:37:41+00:00"
              }
            ],
        "messages": [
            {
              "sent": 1500,
              "delievered": 100,
              "system.error": 0,
              "receiver.error": 2,
              "operator.error": 0,
              "total": 1602
            }
          ]
        },
        {
          "content": "This is a content",
          "createAt": "2016-06-17T18:21:23+00:00",
          "id": 2,
          "lastModifiedAt": "2016-06-17T18:21:23+00:00",
          "title": "This is a title",
          "sender": "Something",
          "status": "created",
          "schedule": null,
          "statuses": [
                {
                    "status": "created",
                    "date": "2016-06-17T18:21:23+00:00"
                }
            ],
        "messages": [
            {
              "sent": 1500,
              "delievered": 100,
              "system.error": 0,
              "receiver.error": 2,
              "operator.error": 0,
              "total": 1602
            }
          ]
        }
    ]
}
```

> Se não houver ações o retorno será o seguinte:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "error": "You don't have any Action yet.",
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
+ items  | Array de ações 


### Listando uma ação

```http
GET /campaigns/ID HTTP/1.1 200 OK
Authorization: Bearer YourTokenComesHere
Content-Type: application/json

{
  "content": "This is a modified",
  "createAt": "2016-06-17T18:21:23+00:00",
  "id": 1,
  "lastModifiedAt": "2016-06-17T18:21:23+00:00",
  "title": "This is a modified",
  "sender": "Modified",
  "status": "created",
  "schedule": "2016-07-12 13:00"
}
```

> Se não houver ação o retorno será o seguinte:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "error": "You don't have any Action yet.",
    "code": 404
}
```

**PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
ID_Account | Sim | O ID irá ser gerado de acordo com a Account que está logada
ID_Campaign | Sim | O ID que será buscada

* Response

Atributo | Descrição
-------- | ---------
+ id | A mesma gerada na criação
+ createdAt  | A mesma gerada na criação
+ modifieddAt  | A mesma gerada na criação
+ content | A mesma usada na criação
+ title | A mesma usada na criação
+ sender | A mesma usada na criação
+ status | A mesma gerada na criação
+ schedule | A mesma gerada na criação

### Excluindo a ação

Para se excluir uma ação é necessário um ID e que o status da ação é seja 'Criado'
```http
DELETE /capaigns/ID HTTP/1.1
Authorization: Bearer YourTokenComesHere
Accept: application/json
User-Agent: Http/2.2
Host: HOST

{

}
```

> Se o ID estiver incorreto o retorno será o seguinte:

```http
HTTP/1.1 404 Unauthorized
Content-Type: application/json

{
    "error": "Action not found.",
    "code": 404
}
```

**PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
ID | Sim | Unique e int
