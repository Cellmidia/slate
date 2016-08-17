# Listas

Visão Geral
-----------

Recursos de listas é a representação de um grupo de contatos que poderá ser criado pelo Cliente.

## Lista

Para criar uma lista deve-se ultilizar o seguinte endpoint:

    `POST /groups`

Para editar uma lista deve-se utilizar o seguinte endpoint:

    `PATCH /groups/ID`
    
Para adicionar um contato à lista deve-se utilizar o seguinte endpoint:

    `PATCH /groups/ID`
    
Para listar todas as listas deve-se utilizar o seguinte endpoint:

    `GET /groups`
 
Para listar uma lista deve-se utilizar o seguinte endpoint:

    `GET /groups/ID`
    
Para deletar uma lista deve-se utilizar o seguinte endpoint:

    `DELETE /groups/ID`
    
### Criando a lista

```http
POST /groups HTTP/1.1
Authorization: Bearer YourTokenComesHere
Accept: application/json
User-Agent: Http/2.2
Host: HOST

{
    "name": "New list",
    "icon": "URL"
}
```

> A solicitação acima retorna a seguinte resposta:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": 1,
  "name": "New list",
  "contacts": "0",
  "createAt": "2016-06-17T18:21:23+00:00",
  "lastModifiedAt": "2016-06-17T18:21:23+00:00",
  "status": "active",
  "icon": "URL"
}
```

> Se a lista estiver incorreta o retorno será o seguinte:

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
    "error": "The name \"invalid\" needs to be between 6 and 128 chars.",
    "code": 409
}
```

O Recurso de ação é composto pelos seguintes atributos

Atributo | Descrição
-------- | ---------
+ id | Representa uma ID
+ createdAt  | Representa a data de criação
+ modifiedAt  | Representa a data de modificação
+ name | Representa o nome da lista
+ icon | Representa o icone da lista
+ contacts | Contador de contatos
+ status | Representa o status da lista


 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
name |  Sim | String entre 6-128 caracteres
icon | Não | URL

#### Response

Atributo | Descrição
-------- | ---------
+ id | Novo ID
+ createdAt  | DateTime atual
+ modifiedAt  | DateTime atual
+ name | A mesma usada na solicitação
+ contacts | Contador de contatos
+ status | A constante ACTIVE
+ url | A mesma usada na solicitação


### Editando a lista

```http
PATCH /groups/ID HTTP/1.1
Authorization: Bearer YourTokenComesHere
Accept: application/json
User-Agent: Http/2.2
Host: HOST

{
    "name": "New edited list"
}
```

> A solicitação acima retorna a seguinte resposta:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": 1,
  "name": "New edited list",
  "contacts": "0",
  "createAt": "2016-06-17T18:21:23+00:00",
  "lastModifiedAt": "2016-06-17T18:21:23+00:00",
  "status": "active",
  "icon": "URL"
}
```
> Se a lista estiver incorreta o retorno será o seguinte:

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
    "error": "The name \"invalid\" needs to be between 6 and 128 chars.",
    "code": 409
}
```

 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
name |  Sim | String entre 6-128 caracteres

#### Response

Atributo | Descrição
-------- | ---------
+ id | O mesmo usada na criação
+ createdAt  | A mesma usada na criação
+ modifiedAt  | A mesma usada na criação
+ name | A mesma usada na solicitação
+ contacts | Contador de contatos
+ status | A mesma usada na criação


### Adicionando contatos à lista

```http
PATCH /groups/ID HTTP/1.1
Authorization: Bearer YourTokenComesHere
Accept: application/json
User-Agent: Http/2.2
Host: HOST

{
    "contacts": [
        1,
        2
    ]
}
```

> A solicitação acima retorna a seguinte resposta:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": 1,
  "name": "New edited list",
  "contacts": "2",
  "createAt": "2016-06-17T18:21:23+00:00",
  "lastModifiedAt": "2016-06-17T18:21:23+00:00",
  "status": "active",
  "icon": "URL"
}
```

 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
groups |  Sim | Array de id's de contatos

#### Response

Atributo | Descrição
-------- | ---------
+ id | O mesmo usada na criação
+ createdAt  | A mesma usada na criação
+ modifiedAt  | A mesma usada na criação
+ name | A mesma usada na solicitação
+ contacts | Contador de contatos
+ status | A mesma usada na criação


### Listando todas as listas


```http
GET /groups HTTP/1.1 200 OK
Authorization: Bearer YourTokenComesHere
Content-Type: application/json

{
    "count": 2,
    "items": [
        {
          "id": 1,
          "name": "New edited list",
          "contacts": "2",
          "createAt": "2016-06-17T18:21:23+00:00",
          "lastModifiedAt": "2016-06-17T18:21:23+00:00",
          "status": "active"
          "icon": "URL"
        },
        {
            "id": 2,
            "name": "New list",
            "contacts": "0",
            "createAt": "2016-06-17T18:21:23+00:00",
            "lastModifiedAt": "2016-06-17T18:21:23+00:00",
            "status": "active"
            "icon": null
        }
    ]
}
```

> Se não houverem listas o retorno será o seguinte:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "error": "You don't have any List yet.",
    "code": 404
}
```

**PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
ID_Account | Sim | O ID irá ser gerado de acordo com a Account que está logada

#### Response

Atributo | Descrição
-------- | ---------
+ count | Contador
+ items  | Array de listas 


### Listando uma lista

```http
GET /groups/ID HTTP/1.1 200 OK
Authorization: Bearer YourTokenComesHere
Content-Type: application/json

{
  "id": 1,
  "name": "New edited list",
  "contacts": "2",
  "createAt": "2016-06-17T18:21:23+00:00",
  "lastModifiedAt": "2016-06-17T18:21:23+00:00",
  "status": "active"
  "icon": "URL"
}
```

> Se não houver nenhuma lista o retorno será o seguinte:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "error": "You don't have any List yet.",
    "code": 404
}
```

**PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
ID_Account | Sim | O ID irá ser gerado de acordo com a Account que está logada
ID_List | Sim | O ID que será buscado

#### Response

Atributo | Descrição
-------- | ---------
+ id | O mesmo usada na criação
+ createdAt  | A mesma usada na criação
+ modifiedAt  | A mesma usada na criação
+ name | A mesma usada na solicitação
+ contacts | Contador de contatos
+ status | A mesma usada na criação
+ icon | A mesma usada na criação

### Excluindo a lista

Para se excluir uma lista é necessário um ID

```http
DELETE /groups/ID HTTP/1.1 200 OK
Authorization: Bearer YourTokenComesHere
Content-Type: application/json
{
    "message": "List deleted succesfully"
}

```

> Se o ID estiver incorreto o retorno será o seguinte:

```http
HTTP/1.1 404 Unauthorized
Content-Type: application/json

{
    "error": "List not found.",
    "code": 404
}
```

**PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
ID | Sim | Unique e int
