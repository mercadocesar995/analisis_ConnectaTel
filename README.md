# 📞 Análisis de Consumo, Calidad de Datos & Segmentación — ConnectaTel

[![Google Colab](https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)](https://colab.research.google.com/drive/1XcuSdxDP9FzGL7_NJFYGAwubH6Ntza8F?usp=sharing)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-7DB0DD?style=for-the-badge&logo=seaborn&logoColor=white)](https://seaborn.pydata.org/)

## 🎯 Objetivo del Proyecto
Analizar los patrones de comportamiento y consumo en una base de **4,000 clientes** y **40,000 registros de uso** en **ConnectaTel**[cite: 1]. El proyecto evalúa la calidad de los datos (nulos, valores centinela e inconsistencias temporales)[cite: 1] y compara la efectividad de las variables demográficas (edad) frente a la intensidad de uso (minutos, mensajes y llamadas) para desarrollar estrategias accionables de **segmentación, upselling, fidelización y prevención de churn**[cite: 1].

---

## 🛠️ Tech Stack & Estructura de Datos
* **Librerías de Análisis:** Python (Pandas, NumPy) para auditoría de calidad, imputación de atípicos y manipulación de datos[cite: 1].
* **Visualización:** Matplotlib y Seaborn para el análisis exploratorio de distribución de consumos e interacciones[cite: 1].
* **Modelos de Datos Relacionales (3 Datasets):**
  * `PLANS`: Tarifas mensuales, límites incluidos y costos por excedentes[cite: 1].
  * `USERS`: Perfil demográfico (edad, ciudad), plan contratado, fecha de registro y cancelación (`churn_date`)[cite: 1].
  * `USAGE`: Logs transaccionales de llamadas (duración) y mensajes (longitud)[cite: 1].

---

## ⚠️ Auditoría & Calidad de Datos (Data Quality)

Se realizó una depuración previa para garantizar decisiones comerciales sobre información confiable[cite: 1]:

* **Valores Centinela:** Se identificó `edad = -999` en 1 registro (0.025% de la base), el cual fue imputado utilizando la mediana de las edades válidas[cite: 1].
* **Tratamiento de Nulos:**
  * `city`: 469 nulos (11.7%) y 96 registros con `?` (2.4%), homogeneizados como valores faltantes[cite: 1].
  * `churn_date`: 3,534 nulos (88.35%), identificados correctamente como clientes activos que no han cancelado el servicio[cite: 1].
  * `date` (USAGE): 50 registros nulos identificados[cite: 1].
  * `duration` / `length`: Los nulos dependen del tipo de servicio (las llamadas no tienen longitud de texto ni los mensajes duración)[cite: 1].
* **Inconsistencias Temporales:** En `reg_date` se detectaron 40 registros con año 2026 (1%), fuera del rango válido (hasta 2024), marcándose como nulos para evitar sesgos temporales[cite: 1].
* **Valores Atípicos (Outliers):** Se identificaron registros de alto consumo que superaban los límites de IQR en llamadas, minutos y mensajes[cite: 1]. Al ser comportamientos reales de *heavy users*, **se conservaron** para identificar al segmento de alto valor[cite: 1].

---

## 📊 Segmentación de Clientes: Demografía vs. Comportamiento

### 1. Segmentación Demográfica (Por Edad)
* **Adultos (30–59 años):** 2,000 clientes (50% de la base)[cite: 1].
* **Jóvenes (<30 años):** 1,200 clientes (25% de la base)[cite: 1].
* **Adultos Mayores (60+ años):** 1,200 clientes (25% de la base)[cite: 1].
> **Hallazgo Clave:** La distribución de los planes Básico y Premium es equivalente entre todos los rangos etarios[cite: 1]. La edad **no explica** la elección del plan ni el nivel de consumo[cite: 1].

### 2. Segmentación por Intensidad de Uso (Comportamiento)
* **Uso Medio:** ~3,000 clientes (75% de la base) — Consumo moderado recurrente[cite: 1].
* **Bajo Uso:** ~800 clientes (20% de la base) — Consumo esporádico o riesgo de desinterés[cite: 1].
* **Alto Uso:** ~300 clientes (5% de la base) — Consumo intensivo que supera los promedios[cite: 1].
> **Hallazgo Clave:** El comportamiento de uso es un **criterio significativamente superior a la edad** para guiar la estrategia comercial[cite: 1]. Los mensajes representan el **55.23%** del uso total frente al **44.77%** de llamadas[cite: 1].

---

## 💡 Insight Ejecutivo & Recomendaciones de Negocio

### 📌 Conclusiones Estratégicas
1. **Línea de Upselling (Alto Uso - 300 usuarios):** Es el segmento más valioso[cite: 1]. Concentra clientes con consumos muy superiores a la media[cite: 1]. Se debe priorizar la migración a planes Premium de aquellos usuarios de alto uso que aún permanecen en el plan Básico[cite: 1].
2. **Línea de Monetización Progresiva (Uso Medio - 3,000 usuarios):** Representa el núcleo del negocio[cite: 1]. Se deben diseñar micro-paquetes adicionales de minutos/mensajes e incentivos para elevar gradualmente su ticket promedio[cite: 1].
3. **Línea de Retención y Activación (Bajo Uso - 800 usuarios):** Se requiere cruzar este grupo con la tasa de cancelación (`churn_date`) para determinar si son clientes con baja necesidad natural o si muestran señales de desinterés previas al abandono[cite: 1].

### 💡 Plan de Acción Recomendado para ConnectaTel
* **Cross-Analysis Plan vs. Uso:** Cruzar inmediatamente el segmento de *Alto Uso* con la tarifa contratada para cuantificar la oportunidad real de conversión de Básico a Premium[cite: 1].
* **Oferta Comercial Flexible:** Reestructurar el catálogo abandonando la segmentación por edad y migrando hacia ofertas personalizadas según la intensidad de uso[cite: 1].
* **Mitigación Focalizada de Churn:** Evaluar diferencias en la cancelación cruzando `grupo_uso`, `plan` y `churn_date` para destinar presupuesto de retención únicamente a los segmentos con evidencia estadística de riesgo[cite: 1].

---

## 🔗 Enlaces del Proyecto

* 💻 **[Ejecutar Notebook en Google Colab](https://colab.research.google.com/drive/1XcuSdxDP9FzGL7_NJFYGAwubH6Ntza8F?usp=sharing)**[cite: 1]
* 📁 **[Explorar Código y Repositorio](./)**
