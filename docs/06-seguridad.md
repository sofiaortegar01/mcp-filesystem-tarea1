# 6. Seguridad en MCP
-La seguridad es especialmente importante cuando un servidor MCP tiene acceso al sistema de archivos, porque una herramienta puede leer, crear, modificar o eliminar información real. 

## Riesgos Concretos

- **Inyección de instrucciones:** Un archivo de texto malicioso podría contener comandos ocultos que engañen al LLM para ejecutar acciones destructivas.
- **Escape de rutas:** Intentos de acceder a directorios superiores (`../../`) fuera del espacio de trabajo autorizado.
- **Modificación o borrado no deseado:** Pérdida de información si el modelo ejecuta operaciones de escritura o eliminación por error.

## Mitigaciones
- Es la barrera crítica de control. Los clientes compatibles con MCP (como Claude Desktop) requieren que el usuario apruebe explícitamente mediante una ventana emergente o un clic cada vez que el modelo intenta ejecutar una herramienta con efectos secundarios (como escribir o modificar un archivo).
- Alcance limitado a un directorio (Allowlist / Sandbox):
El servidor de sistema de archivos se ejecuta confinado a una ruta específica de trabajo que se define estáticamente en el archivo de configuración. Cualquier intento de salir de esa carpeta raíz es bloqueado a nivel de código por el servidor.
- Permisos de solo lectura:
Cuando no se requiere que la IA edite código o cree documentos, se puede configurar el servidor para que exponga únicamente operaciones de lectura e inspección, anulando por completo los riesgos de escritura o borrado.
- Revisión de lo que el servidor expone:
Auditar periódicamente el catálogo de herramientas y recursos que el servidor publica para asegurar que solo estén disponibles las funciones estrictamente necesarias para la tarea.