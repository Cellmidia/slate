---
title: Cellmidia API Reference

language_tabs:
  - shell
  - php

toc_footers:
  - <a href='#'>Cellmidia Developers Team</a>

includes:
  - authorization
  - http_status_code

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

    Todas requisições `GET` e `DELETE` devem ter seus argumentos passados na `QUERY STRING`

API Request
-----------

    A Cellmidia API expõe uma lista de serviços REST para várias ações para a gestão da sua conta, envios de SMS e
    relatórios.

    Todas as requisições devem ser feitas em: `http://api.smsapp.com.br/v1`

API Response
-----------

    Todas as APIs da Cellmidia retornam uma resposta em formato JSON.

    Uma lista dos principais códigos de status HTTP podem ser vista na seção HTTP Status Code.
