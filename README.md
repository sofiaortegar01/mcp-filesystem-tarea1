# mcp-filesystem-tarea1
- **INSTITUTO POLITECNICO NACIONAL**
- **ESCUELA SUPERIOR DE COMPUTO**
- **Nombre Completo:** Sofía Ortega García
- **Boleta:** 2024630517
- **Grupo:** 7CV4
- **Carrera:** Ingeniería en Sistemas Computacionales
Tarea 1: MCP y sistema de archivos

---

##  Resumen de la Actividad
El objetivo principal de esta práctica es comprender cómo un modelo de lenguaje (LLM) pasa de operar en un entorno aislado a interactuar directamente con archivos locales mediante el **Model Context Protocol (MCP)**. Para lograrlo, se realiza una investigación profunda sobre la arquitectura del protocolo, se contrasta con las APIs tradicionales, se implementa y configura localmente un servidor de sistema de archivos (Filesystem MCP) utilizando un directorio seguro de trabajo (*sandbox*), y se validan las operaciones de lectura, escritura, búsqueda y los límites de seguridad correspondientes.

---

##  Índice de Documentación (`docs/`)
La investigación detallada de la tarea se encuentra organizada en la carpeta `docs/` de la siguiente manera:

1. **[Evolución de los Modelos](docs/01-evolucion_de_los_modelos.md)** — Definición de LM y LLM, y cómo surge el razonamiento explícito mediante técnicas de entrenamiento y cómputo en inferencia.
2. **[El Problema del Aislamiento](docs/02-problema_del_aislamiento.md)** — Razones de arquitectura y seguridad por las cuales un LLM estándar no puede acceder directamente al sistema de archivos.
3. **[MCP frente a una API](docs/03-MCP _frente_una_API.md)** — Análisis conceptual y diferencias clave entre una API tradicional y el protocolo MCP.
4. **[Arquitectura de MCP](docs/04-arquitectura_de_mcp.md)** — Descripción del modelo Host/Cliente/Servidor, sus primitivas (tools, resources, prompts), transportes y versión de la especificación.
5. **[El Servidor de Sistema de Archivos](docs/05-el_servidor_de_sistema_de_archivos.md)** — Explicación del servidor de referencia FS, sus herramientas expuestas y la delimitación mediante directorios permitidos.
6. **[Seguridad](docs/006-seguridad.md)** — Análisis de riesgos (inyección de instrucciones, fugas de rutas) y mitigaciones implementadas.
7. **[Casos de Uso](docs/07-casos_de_uso.md)** — Herramientas actuales que implementan MCP para la edición autónoma de repositorios de código.

---
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

---
## Instrucciones de Instalación Paso a Paso (Reproducible en máquina limpia)

### 1. Prerrequisitos
* **Sistema Operativo:** Windows 11 (en Lenovo ThinkPad T480).
* **Node.js:** Versión LTS instalada globalmente (verificado con `node -v`), v24.20.0.

### 2. Estructura de Trabajo Aislada ("Sandbox")
Se creó un directorio específico y controlado para evitar usar la raíz del disco:
`C:\Users\sofia_Ortega\Documents\Aplicaciones moviles nativas\mcp-filesystem-tarea1\mcp-workspace`

### 3. Configuración del Cliente (VS Code)
Se configuró el entorno de desarrollo integrando el servidor MCP oficial de sistema de archivos (`@modelcontextprotocol/server-filesystem`) mediante `npx`. El archivo de configuración utilizado se encuentra respaldado en la carpeta `config/` del repositorio.

---
## Evidencias y Operaciones Realizadas (`img/`)

A continuación se enlistan las evidencias capturadas durante la ejecución práctica:
* **Listado del contenido autorizado :** (Ver `img/01-contenido.png`) Listado inicial de capacidades expuestas por el servidor de archivos.
* **Creación y Modificación:** (Ver `img/02-archivo_nuevo.png`) Creación de nuevos archivos de texto y modificación de su contenido mediante instrucciones al modelo. (Ver `img/02-1-comprobacion.png`)Para la comprobacion del correcto funcionamiento del comando  
* **Lectura y Listado:** (Ver `img/03-leer_archivo.png`) Visualización del contenido del directorio autorizado y lectura del archivo `nota.txt`.
* **Modificación de un archivo**  (Ver `img/04-modificar_archivo.png`) Visualización de la linea agregada  (Ver `img/04-1-modificar_archivo.png`) evidencia del archivo modificiado.
* **Búsqueda:** (Ver `img/05-busqueda.png`) Localización de archivos dentro del workspace.
* **Prueba del Límite de Seguridad:** (Ver `img/06-seguridad.png`) Intento de acceso a rutas fuera del directorio autorizado (`C:\Windows\...`), bloqueado exitosamente por el mecanismo de *allowlist* del servidor y la confirmación de control.

---

## Conclusiones Personales
El uso de Model Context Protocol cambia radicalmente la forma en que interactuamos con los entornos de desarrollo y los datos locales. A diferencia de las APIs tradicionales donde cada flujo de datos debe estar rígido y programado de antemano, MCP otorga al modelo la capacidad de descubrir herramientas de manera autónoma pero bajo un estricto control de seguridad y supervisión humana, evitando riesgos de acceso arbitrario al sistema operativo.

---

## Referencias
* Anthropic. (2026). *Model Context Protocol Specification*. Versión oficial consultada para el desarrollo de la actividad.
* Node.js Foundation. (2026). *Documentación oficial de NPX y gestión de paquetes*. Recuperado de https://nodejs.org/