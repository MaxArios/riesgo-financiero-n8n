📊 Evaluador de Riesgo Financiero (n8n)
🧠 Descripción

Este proyecto implementa un sistema de evaluación de riesgo financiero utilizando n8n, basado en dos variables macroeconómicas:

Riesgo del dólar

Riesgo de la inflación

A partir de estas variables, el flujo determina un riesgo financiero final aplicando reglas lógicas predefinidas.

El objetivo del proyecto es demostrar lógica de negocio, uso de nodos condicionales, merge de datos y documentación técnica, orientado a portfolio.

🎯 Objetivo

Determinar el nivel de riesgo financiero final (ALTO, MEDIO o BAJO) combinando el estado actual del dólar y la inflación.

📥 Variables de entrada
Variable	Valores posibles
riesgo_dolar	ALTO, MEDIO, BAJO
riesgo_inflacion	ALTO, MEDIO, BAJO

Estas variables se generan previamente en el flujo a partir de datos económicos y luego se unifican mediante un nodo Merge.

📤 Variable de salida
Variable	Descripción
riesgo_final	Nivel de riesgo financiero resultante
🧮 Matriz de decisión
Dólar	Inflación	Riesgo final
ALTO	BAJO	ALTO
MEDIO	BAJO	MEDIO
BAJO	ALTO	ALTO
MEDIO	ALTO	ALTO
BAJO	BAJO	BAJO
⚙️ Lógica de decisión

La evaluación del riesgo final se realiza aplicando la siguiente lógica:

Riesgo ALTO

Si riesgo_dolar = ALTO

O si riesgo_inflacion = ALTO

Riesgo MEDIO

Si riesgo_dolar = MEDIO

Y riesgo_inflacion = BAJO

Riesgo BAJO

Si riesgo_dolar = BAJO

Y riesgo_inflacion = BAJO

La prioridad se da siempre al riesgo más alto detectado.

🛠️ Implementación en n8n

Los riesgos individuales se calculan mediante nodos IF

Se unifican con un nodo Merge

La decisión final se realiza con un IF jerárquico:

IF riesgo alto

IF riesgo medio

ELSE → riesgo bajo

El valor final se asigna mediante nodos Set

🧪 Casos de prueba
Dólar	Inflación	Resultado esperado
ALTO	BAJO	ALTO
MEDIO	BAJO	MEDIO
BAJO	ALTO	ALTO
MEDIO	ALTO	ALTO
BAJO	BAJO	BAJO
⚠️ Problemas resueltos

Evitar tomar valores históricos en lugar del dato actual

Corrección de condiciones IF que solo evaluaban igualdad exacta

Manejo correcto de combinaciones distintas (ALTO + BAJO, etc.)

Priorización lógica del riesgo más crítico

🚀 Posibles mejoras

Conexión a APIs económicas en tiempo real

Ponderación numérica de variables

Agregar más indicadores (riesgo país, tasa de interés)

Persistencia de resultados en base de datos

Visualización con dashboard

📌 Tecnologías utilizadas

n8n

Lógica condicional

Flujos automatizados

Documentación técnica para portfolio

👤 Autor

Maximiliano Agustín Ríos Sueldo
Proyecto realizado con fines educativos y de portfolio.
