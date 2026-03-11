# 📡 TelecomX LATAM — Análisis de Evasión de Clientes (Churn)

> Challenge de Data Science | Alura LATAM

---

## 📋 Descripción del Proyecto

Este proyecto analiza el comportamiento de los clientes de **TelecomX**, una empresa de telecomunicaciones en Latinoamérica, con el objetivo de identificar los factores que influyen en el **abandono del servicio (churn)** y proponer estrategias de retención.

El análisis sigue un proceso ETL completo: extracción de datos desde una fuente JSON anidada, transformación y limpieza, y finalmente análisis exploratorio con visualizaciones.

---

## 🎯 Objetivo

Identificar los factores que influyen en el abandono de clientes de TelecomX y proponer recomendaciones estratégicas para reducirlo.

---

## 📁 Estructura del Proyecto

```
TelecomX_LATAM/
│
├── TelecomX_LATAM.ipynb           # Notebook principal con el análisis completo
├── grafico_evasion_cliente.jpg    # Gráfico de distribución de churn
├── grafico_porcentajes.jpg        # Churn por variables categóricas
├── grafico_evasion_varnumeric.jpg # Churn por cargos totales
├── grafico_abandono.jpg           # Tasa de abandono por antigüedad
└── README.md
```

---

## 🗃️ Dataset

- **Fuente:** [Alura Cursos — GitHub](https://raw.githubusercontent.com/alura-cursos/challenge2-data-science-LATAM/refs/heads/main/TelecomX_Data.json)
- **Formato original:** JSON con columnas anidadas (`customer`, `phone`, `internet`, `account`)
- **Registros originales:** 7.267
- **Registros tras limpieza:** 7.032
- **Variables analizadas:** 22
- **Variable objetivo:** `Abandonó_Servicio` (Churn)

### Diccionario de Datos

| Variable | Descripción |
|---|---|
| `ID` | Identificación única del cliente |
| `Abandonó_Servicio` | Si el cliente dejó la empresa (1 = Sí, 0 = No) |
| `Género` | Género del cliente |
| `Cliente_Señor` | Si el cliente tiene 65 años o más |
| `Antigüedad` | Meses de permanencia en la empresa |
| `Servicio_Internet` | Tipo de servicio de internet contratado |
| `Tipo_Contrato` | Modalidad del contrato (Mensual, Anual, Bienal) |
| `Método_Pago` | Forma de pago utilizada |
| `Cargo_Mensual` | Monto facturado mensualmente |
| `Cargo_Total` | Monto total facturado |
| `Cargo_Diario` | Variable derivada: Cargo Mensual / 30 |

---

## ⚙️ Proceso ETL

### 🔵 Extracción
- Carga del dataset en formato JSON desde repositorio GitHub
- Inspección inicial de dimensiones y tipos de datos

### 🟡 Transformación
- Desanidado de columnas JSON con `pd.json_normalize`
- Eliminación de registros con `Churn` vacío y `Charges.Total` no numérico (235 registros)
- Conversión de variables binarias (`Yes`/`No`) → enteros (`1`/`0`)
- Normalización de valores: `No internet service` y `No phone service` → `0`
- Traducción de columnas y valores al español
- Creación de variable derivada `Cargo_Diario`
- Reset de índice para integridad del DataFrame

### 🟢 Carga y Análisis
- Estadísticas descriptivas con `.describe()`
- Visualizaciones de distribución de churn
- Análisis por variables categóricas y numéricas

---

## 📊 Principales Hallazgos

### Tasa de Abandono General

| Categoría | Porcentaje |
|---|---|
| Clientes que permanecieron | 73.42% |
| Clientes que abandonaron | **26.58%** |

> ⚠️ 1 de cada 4 clientes abandona el servicio. Esta tasa supera el umbral crítico del 20%.

### 🔴 Segmentos con Mayor Riesgo de Churn

| Factor | Tasa de Abandono |
|---|---|
| Cheque electrónico (método de pago) | **45.3%** |
| Contrato Mensual | **42.7%** |
| Fibra Óptica | **41.9%** |
| Cliente Senior | **41.7%** |

### 📉 Antigüedad y Churn
Los clientes con **menor antigüedad (0–18 meses)** presentan la mayor tasa de abandono. A mayor tiempo en la empresa, menor probabilidad de churn.

---

## 💡 Recomendaciones Estratégicas

1. **Incentivar contratos de largo plazo** — Los contratos anuales y bienales reducen significativamente el churn.
2. **Revisar la experiencia con Fibra Óptica** — Alta tasa de abandono sugiere problemas de calidad o precio.
3. **Migrar clientes a métodos de pago automáticos** — El cheque electrónico concentra el mayor churn.
4. **Programas de onboarding reforzados** — Los primeros 18 meses son críticos para la retención.
5. **Atención especial a clientes senior** — Segmento con alta tasa de abandono y potencialmente diferente necesidad de soporte.

---

## 🛠️ Tecnologías Utilizadas

- **Python 3**
- **Pandas** — Manipulación y limpieza de datos
- **NumPy** — Operaciones numéricas
- **Matplotlib** — Visualizaciones
- **Seaborn** — Visualizaciones estadísticas
- **Google Colab** — Entorno de ejecución

---

## ▶️ Cómo Ejecutar

Abre el notebook directamente en Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/luceroabanto04-commits/TELECOM_X_ALURA_LATAM/blob/main/TelecomX_LATAM.ipynb)

El dataset se carga automáticamente desde GitHub, no necesitas descargar nada.

---

## 👩‍💻 Autora

**Lucero Abanto**  
Challenge Data Science — Alura LATAM
