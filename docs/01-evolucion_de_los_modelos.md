# 1. Evolución de los Modelos

## ¿Qué es un Modelo de Lenguaje (LM) y cómo evolucionó a un LLM?
- **Modelo de Lenguaje (LM):** Un modelo de lenguaje es un sistema de inteligencia artificial que predice la siguiente palabra o fragmento de texto basándose en análisis estadísticos de grandes volúmenes de datos lingüísticos.
- **Evolución a LLM (Large Language Model):** Los LMs crecieron exponencialmente en parámetros, capacidad de cómputo y tamaño de dataset (entrenados con arquitecturas Transformer), lo que les permitió adquirir capacidades emergentes de comprensión general, traducción y síntesis.

## Modelos con Razonamiento Explícito
- Un modelo con razonamiento explícito es una inteligencia artificial entrenada para descomponer problemas complejos en pasos lógicos intermedios
- Esta capacidad no surge simplemente por "hacer el modelo más grande". 
- Proviene de técnicas de entrenamiento avanzadas (como *Reinforcement Learning from Human Feedback* - RLHF) y de cómputo adicional en el momento de la inferencia (por ejemplo, cadenas de pensamiento o *Chain-of-Thought*, donde el modelo procesa pasos intermedios antes de dar una respuesta final).

# 2. El Problema del Aislamiento

## ¿Por qué un LLM no puede ver ni modificar archivos por sí mismo?
- **Naturaleza técnica:** Un LLM puro es una función matemática de entrada y salida de texto ($Texto \rightarrow Texto$). No ejecuta llamadas directas al sistema operativo ($OS$), ni maneja sockets de archivos locales por defecto.
- **Razones de arquitectura:** Los LLMs suelen ejecutarse en servidores remotos o entornos aislados en la nube, totalmente desconectados del disco duro local de la computadora del usuario.
- **Razones de seguridad:** El aislamiento protege al sistema operativo. Sin barreras, permitir que un texto malicioso controle el disco duro implicaría un riesgo crítico de ejecución arbitraria de código o borrado de datos.