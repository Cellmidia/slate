# Mensagens

Visão Geral
-----------

Recursos de mensagem é a representação de uma mensagem que poderá ser enviada pelo Cliente.


## Mensagem

Para se criar uma mensagem deve-se ultilizar o seguinte endpoint:

    `POST /messages`
    
Para se listar todas as mensagens deve-se ultilizar o seguinte endpoint:

    `GET /messages`
 
Para se listar uma mensagem deve-se ultilizar o seguinte endpoint:

    `GET /messages/ID`    

## Status

Status | Descrição
--------- | -----------
+ CREATED | Mensagem criada
+ SENT | Mensagem enviada
+ DELIVERED | Mensagem entregue
+ SYSTEM_ERROR | Erro de sistema
+ RECEIVER_ERROR | Erro do gateway
+ OPERATOR_ERROR | Erro da operadora telefonica

### Criando mensagem

```http
POST /messages HTTP/1.1
Accept: application/json
User-Agent: Http/2.2
Host: HOST

{
    "message": "This is a message",
    "from": "Something",
    "to": 554899246868,
    "type": "SMS",
}
```

> A solicitação acima retorna a seguinte resposta:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "createAt": "2016-06-17T18:21:23+00:00",
  "from": "Aaa",
  "id": 9,
  "message": "abcdefghigjkl",
  "lastModifiedAt": "2016-06-17T18:21:23+00:00",
  "to": 554899963369,
  "type": "MMS"
}
```
> Se a mensagem estiver incorreta o retorno será o seguinte:

```http
HTTP/1.1 409 Conflict
Content-Type: application/json

{
    "error": "The message \"invalid\" needs to be between 10 and 150 chars.",
    "code": 409
}
```

**MENSAGENS PARA PARAMENTROS INCORRETOS**

Argumento | Mensagem
--------- | -----------
message | The message "invalid" needs to be between 10 and 150 chars.
from | The name "%s" needs to be between 3 and 15 characters.
to | The number %s is a invalid number.
type | The number %s is a invalid number.


O Recurso de Mensagem é composto pelos seguintes atributos

Atributo | Descrição
-------- | ---------
+ id | Representa uma ID
+ createdAt  | Representa a data de criação
+ modifieddAt  | Representa a data de modificação
+ message | Representa o texto da mensagem
+ owner | Representa uma account
+ from | Representa o remetente
+ to | Representa o numero do destinatario
+ type | Representa o tipo de mensagem


 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
message | Sim | Mensagem entre 10 e 150 caracteres
from | Sim | Nome entre 3-15 caracteres
to | Sim | Apenas numeros inteiros
type | Sim | Tipo de mensagem

* Response

Atributo | Descrição
-------- | ---------
+ id | Novo ID
+ createdAt  | DateTime atual
+ modifieddAt  | DateTime atual
+ message | A mesma usada na solicitação
+ from | A mesma usada na solicitação
+ to | A mesma usada na solicitação
+ type | A mesma usada na solicitação


**PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
ID | Sim | Unique e int

### Listando todas as menssagens

```http
GET /messages HTTP/1.1
Accept: application/json
User-Agent: Http/2.2
Host: HOST

{
    
}
```

> Se houver mensagens o retorno será o seguinte:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "count": 2,
    "items": [
        {
          "createAt": "2016-06-17T18:21:23+00:00",
          "from": "Alguem",
          "id": 9,
          "message": "abcdefghigjkl",
          "email": "leonardo@cellmidia.com.br",
          "lastModifiedAt": "2016-06-17T18:21:23+00:00",
          "to": 554899963369,
          "type": "SMS"
        },
        {
          "createAt": "2016-06-17T18:52:31+00:00",
          "from": "Something",
          "id": 10,
          "message": "This is a message",
          "lastModifiedAt": "2016-06-17T18:52:31+00:00",
          "to": 554899393369,
          "type": "MMS"
        }
    ]
}
```

> Se não houver mensagens o retorno será o seguinte:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "error": "You don't have any Message yet.",
    "code": 404
}
```

**PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
ID_Owner | Sim | O ID irá ser gerado de acordo com a Account que está logada

* Response

Atributo | Descrição
-------- | ---------
+ count | Contador
+ items  | Array de messages 


### Detalhes de uma Mensagem

```http
GET /messages/1 HTTP/1.1
Accept: application/json
User-Agent: Http/2.2
Host: HOST
```

> Se houver a mensagem o retorno será o seguinte:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "createAt": "2016-06-17T18:21:23+00:00",
    "from": "User",
    "id": 1,
    "message": "This is a message",
    "lastModifiedAt": "2016-06-17T18:21:23+00:00",
    "to": 554899963369,
    "type": "SMS"
}
```

> Se não houver mensagens com esse ID o retorno será o seguinte:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "error": "Message not found.",
    "code": 404
}
```
**PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
ID_Owner | Sim | O ID irá ser gerado de acordo com a Account que está logada
ID | Sim | ID da Message 

* Response

Atributo | Descrição
-------- | ---------
+ id | Mesmo ID usado na solicitação
+ createdAt  | Dado criado anteriormente 
+ modifieddAt  | Dado criado anteriormente
+ message | Dado criado anteriormente
+ from | Dado criado anteriormente
+ to | Dado criado anteriormente
+ type | Dado criado anteriormente
