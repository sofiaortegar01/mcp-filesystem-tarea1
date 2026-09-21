# 4. Arquitectura de MCP

## Modelo Host / Cliente / Servidor
- **Host:** La aplicación principal que ejecuta el entorno 
En mi caso sera Claude Dektop
- **Cliente:** El componente dentro del host que mantiene la conexión directa con los servidores MCP y traduce las peticiones del modelo al protocolo, en el caso de Claude Dektop el host y el cliente vienen empaquetados juntos 
- **Servidor:** El proceso independiente que expone las capacidades (herramientas, recursos o prompts) a través de MCP.
el Servidor es el paquete oficial de sistema de archivos ejecutado mediante Node.js como un proceso hijo local, el cual es invocado dinámicamente por el cliente mediante el transporte stdio para operar exclusivamente sobre el directorio de trabajo autorizado.

## Primitivas del Servidor
- **Tools (Herramientas):** Funciones ejecutables que el modelo puede invocar para realizar acciones con efectos secundarios (como escribir un archivo).
- **Resources (Recursos):** Datos estáticos o contextuales que el servidor expone para que el modelo los lea (como el contenido de un documento o bitácoras).
- **Prompts (Plantillas):** Guías predefinidas que el servidor ofrece para estructurar interacciones con el usuario.

## Primitivas del Cliente
- **Roots:** Define los directorios o límites raíz a los que el servidor y el modelo tienen permitido acceder.
- **Elicitation:** Mecanismos donde el cliente puede solicitar información o confirmación adicional al usuario antes de proceder.

## Transportes de MCP
- **stdio:** Transporte local basado en la entrada y salida estándar del sistema operativo. El servidor corre como un proceso hijo del cliente.
- **Streamable HTTP:** Transporte pensado para servidores remotos mediante flujos HTTP.

## Versión de la Especificación
- La especificación consultada corresponde a la versión oficial de Anthropic Model Context Protocol vigente a 2026.
2026-07-28, publicada el 28 de julio de 2026. Es la revisión actual que aparece como final en la documentación oficial.

