# 3. MCP frente a una API

## ¿Qué es una API?
API significa Application Programming Interface o Interfaz de Programación de Aplicaciones.
Una API es un medio de comunicación que permite que un programa le pida algo a otro programa siguiendo ciertas reglas.
La API establece cosas como:

qué operaciones existen,
qué datos debes enviar,
cómo debes enviarlos,
qué respuesta recibirás,
cómo autenticarte.

Por eso una API funciona como un contrato de comunicación entre dos sistemas.

## ¿Qué es MCP (Model Context Protocol)?
MCP significa Model Context Protocol.

Es un protocolo diseñado para permitir que una aplicación de IA pueda descubrir y utilizar herramientas y recursos externos de una manera estandarizada.
MCP ofrece un método documentado y estandarizado para que un programa informático pueda integrar servicios de una fuente externa. Es compatible con la IA agéntica (programas inteligentes que pueden seguir objetivos y actuar de forma autónoma).


## Tabla Comparativa

| Aspecto | API Tradicional | Model Context Protocol (MCP) |
| :--- | :--- | :--- |
| **¿Quién decide qué se invoca?** | El programador (hardcodeado en el software). | El LLM de forma dinámica en tiempo de ejecución. |
| **¿Cómo se descubren capacidades?** | Mediante documentación estática leída por humanos. | MCP permite descubrir las herramientas y capacidades que expone un servidor MCP. |
| **Acoplamiento cliente-servicio** | Alto; el cliente debe conocer esquemas específicos de cada API. | Bajo y estandarizado mediante el protocolo JSON-RPC. |
| **Formato de los mensajes** | Variado (REST/JSON, SOAP, GraphQL, etc.). | Estandarizado bajo JSON-RPC 2.0. |
| **Autenticación y consentimiento** | La define la API: API keys, OAuth, tokens, sesiones, etc. | SuMCP contempla mecanismos de autorización/autenticación según el transporte y la implementación; |
| **Consentimiento** | Depende de cómo esté diseñada la aplicación y de la operación. | Puede incorporarse control y consentimiento del usuario para acciones realizadas mediante herramientas, especialmente cuando tienen efectos importantes.|
| **Reutilización** | Requiere crear clientes o wrappers específicos para cada API. | Un cliente compatible con MCP puede hablar con cualquier servidor MCP. |
| **Objetivo principal** | Permitir que programas se comuniquen entre sí. | Estandarizar cómo aplicaciones de IA descubren y utilizan herramientas, recursos y capacidades externas. | 

## Aclaración Importante
MCP **no sustituye a las APIs**. Un servidor MCP casi siempre actúa como una capa superior ("wrapper") que envuelve una API existente o un recurso local, haciéndolo descubrible y estructurado para que un modelo de lenguaje lo entienda y utilice de forma segura.