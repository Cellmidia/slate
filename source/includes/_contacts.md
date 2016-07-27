# Contatos

Visão Geral
-----------

Recursos de contatos é a representação de uma contato que poderá ser importado pelo Cliente.


## Contato

Para se criar um contato deve-se ultilizar o seguinte endpoint:

    `POST /contacts`

Para se editar um contato deve-se ultilizar o seguinte endpoint:

    `PATCH /contacts/ID`
    
Para se listar todos os contato deve-se ultilizar o seguinte endpoint:

    `GET /contacts`
 
 Para se listar um contato deve-se ultilizar o seguinte endpoint:
 
     `GET /contacts/ID`

### Criando contato

```http
POST /contacts HTTP/1.1
Authorization: Bearer YourTokenComesHere
Accept: application/json
User-Agent: Http/2.2
Host: api.cellmidia.com.br

{
    "name": "Leonardo",
    "email": "leonardo@cellmidia.com.br",
    "phone": "554899999999"
}
```

> A solicitação acima retorna a seguinte resposta:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": 1,
  "name": "Leonardo",
  "email": "leonardo@cellmidia.com.br",
  "phone": "554899999999",
  "createAt": "2016-06-17T18:21:23+00:00",
  "lastModifiedAt": "2016-06-17T18:21:23+00:00",
  "status": "active"
}
```
> Se o contato estiver incorreta o retorno será o seguinte:

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
    "error": "The name \"None\" needs to be between 4 and 60 chars.",
    "code": 409
}
```

**CONTATO PARA PARAMENTROS INCORRETOS**

Argumento | Mensagem
--------- | -----------
name | The name "invalid" needs to be between 4 and 60 chars.
email | The email "invalid" needs to be between 10 and 60 chars.
phone | The phone "invalid" needs to be between 10 and 15 chars.


O Recurso de Contato é composto pelos seguintes atributos

Atributo | Descrição
-------- | ---------
+ id | Representa uma ID
+ name | Representa o nome do contato
+ email | Representa o email do contato
+ phone | Representa o celular do contato
+ createdAt  | Representa a data de criação
+ modifiedAt  | Representa a data de modificação
+ status | Representa o status do contato


 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
name |  Sim | String entre 4-60 caracteres
email | Sim | String entre 10-60 caracteres
phone | Sim | Int entre 10-15 caracteres 

* Response

Atributo | Descrição
-------- | ---------
+ id | Novo ID
+ createdAt  | DateTime atual
+ modifiedAt  | DateTime atual
+ name | A mesma usada na solicitação
+ email | A mesma usada na solicitação
+ phone | A mesma usada na solicitação
+ status | String "active"

### Editando contato

```http
PATCH /contacts/ID HTTP/1.1
Authorization: Bearer YourTokenComesHere
Accept: application/json
User-Agent: Http/2.2
Host: HOST

{
    "name": "Leonardo Novo",
    "email": "leonardo@cellmidia.com.br",
    "phone": "554899999999"
}
```

> A solicitação acima retorna a seguinte resposta:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "createAt": "2016-06-17T18:21:23+00:00",
  "id": 1,
  "lastModifiedAt": "2016-06-17T18:21:23+00:00",
  "name": "Leonardo Novo",
  "email": "leonardo@cellmidia.com.br",
  "phone": "554899999999",
  "status": "active"
}
```
> Se o contato estiver incorreta o retorno será o seguinte:

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
    "error": "The name \"None\" needs to be between 4 and 60 chars.",
    "code": 409
}
```

**CONTATO PARA PARAMENTROS INCORRETOS**

Argumento | Mensagem
--------- | -----------
name | The name "invalid" needs to be between 4 and 60 chars.
email | The email "invalid" needs to be between 10 and 60 chars.
phone | The phone "invalid" needs to be between 10 and 15 chars.



 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
name |  Não | String entre 4-60 caracteres
email | Não | String entre 10-60 caracteres
phone | Não | Int entre 10-15 caracteres 

* Response

Atributo | Descrição
-------- | ---------
+ id | A mesma gerada na criação
+ createdAt  | A mesma gerada na criação
+ modifiedAt  | A mesma gerada na criação
+ name | A mesma usada na solicitação
+ email | A mesma usada na solicitação
+ phone | A mesma usada na solicitação
+ status | A mesma gerada na criação

### Listando todas os contatos

```http
GET /contacts HTTP/1.1
Authorization: Bearer YourTokenComesHere
Accept: application/json
    "count": 2,
    "items": [
        {
          "createAt": "2016-06-17T18:21:23+00:00",
          "id": 1,
          "lastModifiedAt": "2016-06-17T18:21:23+00:00",
          "name": "Leonardo Novo",
          "email": "leonardo@cellmidia.com.br",
          "phone": "554899999999",
          "status": "active"
        },
        {
          "createAt": "2016-06-17T18:21:23+00:00",
          "id": 2,
          "lastModifiedAt": "2016-06-17T18:21:23+00:00",
          "name": "Leonardo",
          "email": "leonardo@cellmidia.com.br",
          "phone": "554899999999",
          "status": "active"
        }
    ]
}
```

> Se não houver contatos o retorno será o seguinte:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "error": "You don't have any Contacts yet.",
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
+ items  | Array de contatos 

### Listando um contato

```http
GET /contacts/1 HTTP/1.1
Authorization: Bearer YourTokenComesHere
Accept: application/json
{
   "createAt": "2016-06-17T18:21:23+00:00",
   "id": 1,
   "lastModifiedAt": "2016-06-17T18:21:23+00:00",
   "name": "Leonardo Novo",
   "email": "leonardo@cellmidia.com.br",
   "phone": "554899999999",
   "status": "active"
}
```

> Se não houver contatos o retorno será o seguinte:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "error": "You don't have any Contacts yet.",
    "code": 404
}
```

**PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
ID | Sim | ID do contato que foi gerado

* Response

Atributo | Descrição
-------- | ---------
+ id | A mesma gerada na criação
+ createdAt  | A mesma gerada na criação
+ modifiedAt  | A mesma gerada na criação
+ name | A mesma gerada na criação
+ email | A mesma gerada na criação
+ phone | A mesma gerada na criação
+ status | A mesma gerada na criação
