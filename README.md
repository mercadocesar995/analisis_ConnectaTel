# 📞 Análisis de Consumo & Segmentación de Clientes — ConnectaTel

[![Google Colab](https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)](https://colab.research.google.com/drive/1XcuSdxDP9FzGL7_NJFYGAwubH6Ntza8F?usp=sharing)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-7DB0DD?style=for-the-badge&logo=seaborn&logoColor=white)](https://seaborn.pydata.org/)

## 🎯 Objetivo del Proyecto
Analizar los patrones de comportamiento y consumo en una base de **4,000 clientes** y **40,000 registros de uso** en **ConnectaTel**. El proyecto evalúa la efectividad de las variables demográficas (como la edad) frente a la intensidad de uso (minutos, datos y mensajes) para desarrollar criterios accionables de **segmentación, upsell y retención de clientes**.

---

## 🛠️ Tech Stack & Estructura de Datos
* **Librerías de Análisis:** Python (Pandas, NumPy) para procesamiento tabular e imputación de atípicos.
* **Visualización:** Matplotlib y Seaborn para el análisis exploratorio de distribución de consumos.
* **Modelos de Datos Relacionales (3 Datasets):**
  * `Planes`: Tarifas mensuales, límites incluidos y costos excedentes por servicio.
  * `Usuarios`: Perfil demográfico, plan contratado y estado de cancelación (*churn*).
  * `Uso`: Logs transaccionales de llamadas, mensajes y consumo de datos.

---

## 📊 Metodología & Proceso Analítico

```text
1. Exploración & Nulos  ──> 2. Tratamiento de Atípicos ──> 3. Segmentación Dual ──> 4. Análisis de Negocio
   (40k logs de uso)         (Imputación de edad -999)      (Edad vs. Intensidad)     (Upsell & Churn)
