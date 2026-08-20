# analisis_ConnectaTel

## Análisis de Clientes y Consumo — ConnectaTel
🎯 Objetivo del proyecto

Este proyecto analiza el comportamiento de 4.000 clientes y 40.000 registros de uso de ConnectaTel con el objetivo de identificar patrones de consumo, segmentar clientes según su nivel de uso y detectar oportunidades que puedan apoyar la toma de decisiones comerciales.

El análisis busca determinar si variables demográficas como la edad permiten explicar el comportamiento de los clientes y evaluar si la intensidad de uso de los servicios puede ser un criterio más útil para identificar oportunidades de segmentación, upselling y retención.

## Datasets utilizados

### El proyecto utiliza tres datasets principales:

**plans**

Contiene la información de los planes ofrecidos por ConnectaTel:

plan_name: nombre del plan.
messages_included: mensajes incluidos.
gb_per_month: GB incluidos al mes.
minutes_included: minutos incluidos.
usd_monthly_pay: tarifa mensual.
usd_per_gb: costo por GB adicional.
usd_per_message: costo por mensaje adicional.
usd_per_minute: costo por minuto adicional.


**users**

Contiene información demográfica y contractual de los clientes:

user_id: identificador del cliente.
first_name / last_name: nombre y apellido.
age: edad.
city: ciudad.
reg_date: fecha de registro.
plan: plan contratado.
churn_date: fecha de cancelación, cuando corresponde.


**usage**

Contiene el detalle de las interacciones realizadas por los clientes:

id: identificador del registro.
user_id: cliente asociado.
type: tipo de interacción.
date: fecha de la interacción.
duration: duración de la llamada.
length: longitud del mensaje.

## Etapas del análisis

El proyecto se desarrolló en las siguientes etapas:

1. Exploración inicial
Revisión de estructura y dimensiones de cada dataset.
Identificación de tipos de datos.
Revisión de valores nulos y posibles valores atípicos.
Validación de consistencia de las variables.

2. Limpieza y transformación
Conversión de reg_date, churn_date y date al formato datetime.
Revisión de valores faltantes según el significado de cada variable.
Identificación y tratamiento del valor inválido -999 en age, reemplazándolo por la mediana de las edades válidas.
Revisión de valores extremos en las variables de consumo.
Conservación de los valores altos de consumo cuando fueron considerados comportamientos reales de clientes.

3. Análisis exploratorio

Se analizaron los principales patrones de consumo relacionados con:

Mensajes enviados.
Llamadas realizadas.
Minutos de llamadas.
Distribución del consumo.
Diferencias entre los planes Básico y Premium.

4. Segmentación por edad

Los clientes fueron agrupados en tres segmentos:

Jóvenes: menores de 30 años.
Adultos: entre 30 y 59 años.
Adultos Mayores: 60 años o más.

Se evaluó la distribución de clientes y su relación con los planes contratados.

5. Segmentación por nivel de uso

Los clientes fueron clasificados según su intensidad de uso en:

Bajo uso
Uso medio
Alto uso 

6. Análisis ejecutivo y recomendaciones

Finalmente, los resultados fueron traducidos en hallazgos y recomendaciones orientadas a negocio, priorizando:

Identificación de oportunidades de upselling.
Profundización de la segmentación por comportamiento.
Análisis de la relación entre nivel de uso y churn.
Identificación de oportunidades de activación o retención.


## Cómo ejecutar el proyecto
Opción 1 — Google Colab https://colab.research.google.com/drive/1XcuSdxDP9FzGL7_NJFYGAwubH6Ntza8F?usp=sharing

Ingresa a Google Colab.

Selecciona Archivo → Abrir notebook → Subir.

Carga el archivo .ipynb.

Ejecuta las celdas en orden desde el inicio hasta el final.
