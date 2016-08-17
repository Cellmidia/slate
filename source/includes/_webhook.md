# Webhook

Visão Geral
-----------

Recursos de Webhook é a representação de respostas enviadas pelo gateway


## Webhook

Para enviar o status de uma mensagem deve-se utilizar o seguinte endpoint:

    `POST /webhook/zenvia/delivered`
    
Para enviar a resposta de uma mensagem deve-se utilizar o seguinte endpoint:

    `POST /webhook/zenvia/response`
 
### Enviar status

```http
POST  /webhook/zenvia/delivered HTTP/1.1
Origin: https://www.zenvia360.com.br/
Host: Zenvia

{
  "callbackMtRequest": {
    "status": "03",
    "statusMessage": "Delivered",
    "statusDetail": "120",
    "statusDetailMessage": "Message received by mobile",
    "id": "hs765939216",
    "received": "2014-08-26T12:55:48.593-03:00",
    "mobileOperatorName": "Claro"
  }
}
```

> A solicitação acima retorna a seguinte resposta:

```http
HTTP/1.1 204 HTTP_NO_CONTENT
Content-Type: application/json

{

}
```

 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
callbackMoRequest | Sim | Objeto fornecido pelo gateway

### Enviar resposta

```http
POST  /webhook/zenvia/response HTTP/1.1
Origin: https://www.zenvia360.com.br/
Host: Zenvia

{
  "callbackMoRequest": {
    "id": "20690090",
    "mobile": "555191951711",
    "shortCode": "40001",
    "account": "zenvia.envio ",
    "body": "Conteudo do SMS respondido",
    "received": "2014-08-26T12:27:08.488-03:00",
    "correlatedMessageSmsId": "hs765939061"
  }
}
```

> A solicitação acima retorna a seguinte resposta:

```http
HTTP/1.1 204 HTTP_NO_CONTENT
Content-Type: application/json

{
}
```

 **PARÂMETROS DO PAYLOAD**

Argumento | Obrigatório | Observações
--------- | ----------- | -----------
callbackMoRequest | Sim | Objeto fornecido pelo gateway
