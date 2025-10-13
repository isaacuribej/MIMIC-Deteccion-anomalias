# 📌 Proyecto: Detección de Datos Atípicos en MIMIC-III
## 👨‍💻 Autores

- Isaac Esteban Uribe



## 🎯 Objetivo

El objetivo de este proyecto es identificar y analizar datos atípicos en registros clínicos de la base de datos MIMIC-III, con el fin de:

Detectar condiciones clínicas simuladas mediante reglas basadas en biomarcadores.

Complementar los métodos de detección de outliers para mejorar la calidad de los resultados.

Proponer un manejo de los datos faltantes y la estructuración del dataset para futuros análisis.

🗂️ **Estructura del repositorio**

📁 nombre-del-repositorio/  
│  
├── 📁 articulo/  
│   ├── informe_1_nombre_apellidos.pdf  
│   ├── informe_XX_nombre_apellidos.pdf  
│   └── informe_final_nombre_apellidos.pdf  
│  
├── 📁 proyecto_aula/  
│   ├── py_nombre_apellidos_01_intro.ipynb  
│   ├── py_nombre_apellidos_02_limpieza.ipynb  
│   └── py_nombre_apellidos_XX_nombre.ipynb  
│  
├── 📁 sesiones_practicas/  
│   ├── sc_1_nombre_apellidos.ipynb  
│   ├── sc_2_nombre_apellidos.ipynb  
│   └── sc_XX_nombre_apellidos.ipynb  
│  
├── 📁 datos/  
│   └── dataset_procesado.csv  
│  
├── 📁 recursos/  
│   └── referencias_bibliograficas.pdf  
│  
└── README.md  


## 📊 Descripción de la base de datos

La base de datos utilizada es MIMIC-III, que contiene 9,028,427 registros y 15 columnas.

| Variable              | Descripción breve                   | Tipo / Codificación  | Significado clínico principal    |
| --------------------- | ----------------------------------- | -------------------- | -------------------------------- |
| SUBJECT_ID            | Identificador único de paciente     | int64                | Identifica al paciente           |
| HADM_ID               | Identificador de hospitalización    | int64                | Episodio de ingreso hospitalario |
| CHARTTIME             | Marca temporal del registro         | timestamp/string     | Cuándo se tomó el dato           |
| HEART_RATE_VALUE      | Frecuencia cardíaca (lat/min)       | float64              | Evalúa ritmo cardíaco            |
| TEMPERATURE_VALUE     | Temperatura corporal                | float64              | Evalúa fiebre o hipotermia       |
| OXYGEN_SAT_VALUE      | Saturación de oxígeno en sangre (%) | float64              | Evalúa nivel de oxigenación      |
| BLOOD_SYSTOLIC_VALUE  | Presión arterial sistólica (mmHg)   | float64              | Evalúa presión máxima            |
| BLOOD_DIASTOLIC_VALUE | Presión arterial diastólica (mmHg)  | float64              | Evalúa presión mínima            |
| GLUCOSE_VALUE         | Nivel de glucosa (mg/dL)            | numérico tipo string | Evalúa control glucémico         |


| Condición                         | Basada en columna(s)                            | Regla simplificada               |
| --------------------------------- | ----------------------------------------------- | -------------------------------- |
| **Diabetes tipo 2 (sospecha)**    | `GLUCOSE_VALUE`                                 | ≥ 200 mg/dL en cualquier momento |
| **Hipoglucemia**                  | `GLUCOSE_VALUE`                                 | < 70 mg/dL                       |
| **Apnea respiratoria (sospecha)** | `OXYGEN_SAT_VALUE`                              | ≤ 88% en reposo                  |
| **Hipertensión**                  | `BLOOD_SYSTOLIC_VALUE`, `BLOOD_DIASTOLIC_VALUE` | ≥ 140/90 mmHg                    |
| **Hipotensión**                   | `BLOOD_SYSTOLIC_VALUE`, `BLOOD_DIASTOLIC_VALUE` | < 90 / 60 mmHg                   |
| **Taquicardia**                   | `HEART_RATE_VALUE`                              | > 100 bpm                        |
| **Bradicardia**                   | `HEART_RATE_VALUE`                              | < 60 bpm                         |
| **Fiebre**                        | `TEMPERATURE_VALUE`                             | ≥ 38 °C (100.4 °F)               |
| **Hipotermia**                    | `TEMPERATURE_VALUE`                             | < 35 °C (95 °F)                  |


## ▶️ Cómo ejecutar el proyecto
### 1. Requisitos previos

- Python 3.9+

Librerías necesarias:

-!pip install numpy pandas matplotlib seaborn scipy

### 2. Descarga del dataset

Este proyecto utiliza la base de datos MIMIC-III Clinical Database, disponible únicamente bajo credenciales de acceso en:
🔗 https://physionet.org/content/mimiciii/1.4/

### ⚠️ Nota: Debido a su gran tamaño (más de 20 GB), el dataset completo no se incluye en este repositorio.

En su lugar, proporcionamos un archivo reducido de ejemplo en la carpeta:
data se encuentra df_merged_acotado, por lo que una de las celdas no marcara que tiene 9 millones de registros sino que si se corre apareceran 100k reducido a 100k, por lo quen o debe haber preocupación
