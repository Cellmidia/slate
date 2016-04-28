# HTTP Status Code

A Cellmidia API em qualquer solicitação os seguites HTTP Status podem ser retornados:

 Código | Descrição
 ------ | ---------
 200 | Ok -- Sua requisição foi bem sucedida
 201 | Created -- Um novo item foi criado.
 202 | Accepted -- O item corrente foi atualizado.
 204 | No Content -- O item foi apagado.
 400 | Bad Request -- Seu pedido foi mal feito, falta de parâmetro(s) ou parâmetro(s) inválido.
 401 | Unauthorized - Sua API Key contém erro ou autenticação incorreta.
 403 | Forbidden --  O recurso solicitdo é restrito a administradores somente.
 404 | Not Found -- O Recurso pedido não foi encontrado.
 405 | HTTP method not allowed -- Esse recurso não pode ser acessado desta maneira.
 406 | Not Acceptable -- Seu pedido está em um formato não reconhecido.
 409 | Conflict -- Pedido conflitante.
 410 | Gone -- O recurso solicitado foi removido dos nossos servidores.
 418 | I'm a teapot
 429 | Too Many requests -- Vai com calma! Você está fazendo muitos pedidos ao mesmo tempo.
 500 | Internal Server error -- Desculpe-nos mas estamos com problemas em nossos servidores. Tente mais tarde.
 503 | Service Unavailable -- Estamos temporariamente offline para manutenções. Por favor tente mais tarde.
