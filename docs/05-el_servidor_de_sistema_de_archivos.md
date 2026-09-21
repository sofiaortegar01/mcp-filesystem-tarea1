# 5. El Servidor de Sistema de Archivos (FS)

## Naturaleza del Servidor FS
- FS significa File System o sistema de archivos.
- "FS" no forma parte estricta de la especificación central del protocolo; es **uno de los servidores de referencia oficiales** diseñados para interactuar con archivos locales.
-"FS" no es una parte o componente obligatorio del protocolo MCP.
-MCP define cómo se comunican el cliente y el servidor y cómo se describen capacidades como tools, resources y prompts. No define que todos los servidores MCP tengan que trabajar con archivos.

## Herramientas y Alcance
- Expone herramientas para listar directorios: Muestra los archivos y carpetas que existen dentro de un directorio.
- Leer el archivo: Obtiene el contenido de un archivo.
- Escribir el archivo: Modifica o reemplaza el contenido de un archivo existente.
- Crear. Crea un nuevo archivo o carpeta
- Mover un archivo: Cambia un archivo o carpeta de ubicación.
- Buscar archivos: Busca archivos o carpetas que coincidan con determinados criterios.
- **Delimitación de alcance:** Se restringe estrictamente a un directorio de trabajo específico configurado previamente. Sin este límite, el LLM (y cualquier instrucción maliciosa inyectada) podría comprometer todo el sistema de archivos del usuario.
- **Idea clave: **
MCP define la comunicación; FS proporciona las herramientas de archivos; los directorios permitidos delimitan hasta dónde pueden actuar esas herramientas.