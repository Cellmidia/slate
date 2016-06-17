# Mensagens

Visão Geral
-----------

Recursos de mensagem é a representação de uma mensagem que poderá ser enviada pelo Cliente.


## Mensagem

Para se criar uma mensagem deve-se ultilizar o seguinte endpoint:

    `POST /messages`

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
    "schedule": null
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
  "schedule": null,
  "to": 554899963369,
  "type": "MMS"
}
```
> Se a mensagem estiver incorreta o retorno será o seguinte:

```http
HTTP/1.1 401 Unauthorized
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
schedule | Invalid date "%s"


O Recurso de Mensagem é composto pelos seguintes atributos

Atributo | Descrição
-------- | ---------
+ identifier | Representa uma ID
+ timestampable  | Representa a data de criação e de modificação


 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
message | Sim | Mensagem entre 10 e 150 caracteres
from | Sim | Nome entre 3-15 caracteres
to | Sim | Apenas numeros inteiros
type | Sim | Tipo de mensagem
schedule | Não | DateTime não obrigatoria 
