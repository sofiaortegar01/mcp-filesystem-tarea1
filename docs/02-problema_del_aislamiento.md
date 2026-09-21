# 2. El Problema del Aislamiento

## ¿Por qué un LLM no puede ver ni modificar archivos por sí mismo?
Un LLM (Large Language Model),por sí mismo, no puede ver ni modificar archivos porque su función principal es procesar texto y generar texto; no tiene acceso directo al sistema operativo ni al disco del usuario. Además, aunque se le proporcionen herramientas para trabajar con archivos, estas deben estar aisladas y controladas mediante permisos y consentimiento, debido a riesgos como el acceso no autorizado y la inyección de instrucciones.
- **Naturaleza técnica:** Un LLM puro es una función matemática de entrada y salida de texto ($Texto \rightarrow Texto$). No ejecuta llamadas directas al sistema operativo ($OS$), ni maneja sockets de archivos locales por defecto.
- **Razones de arquitectura:** Los LLMs suelen ejecutarse en servidores remotos o entornos aislados en la nube, totalmente desconectados del disco duro local de la computadora del usuario.
- **Razones de seguridad:** El aislamiento protege al sistema operativo. Sin barreras, permitir que un texto malicioso controle el disco duro implicaría un riesgo crítico de ejecución arbitraria de código o borrado de datos.