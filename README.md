# 📊 NovaRetail+ — Drivers de comportamiento de clientes

Análisis exploratorio de los factores de comportamiento asociados con el ingreso anual generado por los clientes de **NovaRetail+**, una plataforma de comercio electrónico en Latinoamérica.

El objetivo principal del proyecto es responder:

> **¿Qué factores del comportamiento del cliente están más fuertemente asociados con el ingreso anual generado?**

Este proyecto utiliza un enfoque **correlacional y exploratorio** para identificar relaciones entre variables de comportamiento, características de los clientes e ingreso anual.

> ⚠️ **Importante:** correlación no implica causalidad. Las asociaciones encontradas permiten identificar patrones, pero no demuestran relaciones de causa y efecto.

---

## 🎯 Objetivo del proyecto

El análisis busca identificar qué características y comportamientos de los clientes presentan una mayor asociación con `ingreso_anual`.

Para ello se estudian variables como:

* Frecuencia de compras.
* Número de visitas mensuales.
* Gasto en publicidad dirigida.
* Nivel de satisfacción.
* Membresía premium.
* Región.
* Tipo de dispositivo.
* Nivel de ingreso.
* Edad.

---

## 📁 Dataset

El conjunto de datos contiene **15.000 registros y 12 variables**.

### Variables principales

| Variable                    | Descripción                                           |
| --------------------------- | ----------------------------------------------------- |
| `id_cliente`                | Identificador único del cliente                       |
| `edad`                      | Edad del cliente                                      |
| `nivel_ingreso`             | Ingreso anual estimado del cliente                    |
| `visitas_mes`               | Número de visitas mensuales                           |
| `compras_mes`               | Número de compras realizadas al mes                   |
| `gasto_publicidad_dirigida` | Gasto en publicidad asignado al usuario               |
| `satisfaccion`              | Nivel de satisfacción del cliente, escala 1–5         |
| `miembro_premium`           | Indicador de membresía premium (0/1)                  |
| `abandono`                  | Indicador de abandono de la plataforma (0/1)          |
| `tipo_dispositivo`          | Dispositivo utilizado: móvil, escritorio o tablet     |
| `region`                    | Región geográfica del cliente                         |
| `ingreso_anual`             | Ingreso anual generado por el cliente para la empresa |

La métrica principal del análisis es **`ingreso_anual`**.

---

## 🔎 Metodología

El análisis se desarrolló en varias etapas:

### 1. Exploración y preparación de datos

* Carga y revisión inicial del dataset.
* Verificación de tipos de datos.
* Revisión de valores faltantes.
* Análisis de variables numéricas, binarias y categóricas.
* Corrección del tipo de dato de `edad`.
* Análisis de estadísticas descriptivas.

El dataset no presenta valores nulos y contiene 15.000 registros completos.

### 2. Análisis exploratorio

Se analizaron las distribuciones y características de las principales variables.

Entre los resultados iniciales destaca que:

* La edad promedio es de aproximadamente **38 años**.
* El promedio de visitas mensuales es de aproximadamente **10**.
* El promedio de compras mensuales es de **1,21**.
* La satisfacción promedio es de **3,60/5**.
* El ingreso anual presenta una dispersión elevada.

En las variables categóricas, el **65,45 % de los clientes utiliza móvil**, seguido por escritorio con 24,80 % y tablet con 9,75 %.

### 3. Visualización de relaciones

Se utilizaron gráficos de dispersión, matrices de correlación y otras visualizaciones para identificar patrones entre las variables.

### 4. Análisis de correlación

Se utilizaron diferentes técnicas dependiendo del tipo de variable:

* **Pearson:** relaciones lineales entre variables numéricas.
* **Spearman:** relaciones monótonas.
* **Punto-biserial:** relación entre variables numéricas y binarias.
* **V de Cramér:** asociación entre variables categóricas.

---

## 📈 Principales resultados

### 🥇 Compras mensuales: principal asociación

La relación más fuerte encontrada fue entre `compras_mes` e `ingreso_anual`.

**Pearson = 0,9671**

La relación es positiva y muy fuerte. El análisis reporta un **R² ≈ 0,94**, lo que indica una asociación extremadamente elevada entre ambas variables.

**Implicación:** la frecuencia de compra aparece como el indicador de comportamiento más relacionado con el valor económico del cliente.

Sin embargo, debido a la magnitud excepcional de esta relación, el propio análisis recomienda **auditar la relación entre ambas variables**, ya que podrían existir redundancias o una fórmula directa entre ellas.

---

### 👀 Visitas mensuales: asociación débil

`visitas_mes` presenta una asociación positiva pero débil con `ingreso_anual`.

**Pearson = 0,3371**

El análisis muestra una alta dispersión, por lo que las visitas por sí solas no explican una gran proporción de la variabilidad del ingreso.

**Implicación:** aumentar el tráfico no necesariamente significa aumentar los ingresos. La conversión de visitas en compras parece ser un aspecto más relevante.

---

### 📢 Publicidad dirigida: asociación muy débil

La relación entre `gasto_publicidad_dirigida` e `ingreso_anual` fue:

**Pearson = 0,1975**

La relación es positiva, pero muy débil, con una elevada dispersión de los datos.

**Implicación:** el gasto en publicidad dirigida no aparece como un indicador fuerte del ingreso anual dentro de este conjunto de datos.

---

### ⭐ Satisfacción: asociación prácticamente nula

La relación entre `satisfaccion` e `ingreso_anual` fue:

**Pearson = 0,0562**

El análisis no encuentra una asociación relevante entre satisfacción e ingresos.

**Implicación:** la satisfacción, al menos medida mediante esta variable, no parece ser un buen indicador del desempeño económico del cliente.

---

### 💎 Membresía Premium

La membresía premium presenta asociaciones muy débiles con las principales variables de comportamiento.

En particular:

* Premium vs. `ingreso_anual`: **0,0931**
* Premium vs. `compras_mes`: **0,0034**
* Premium vs. `visitas_mes`: **-0,0127**

Los resultados sugieren que los clientes premium y no premium presentan comportamientos similares dentro del dataset.

**Implicación:** sería conveniente revisar la propuesta de valor y el funcionamiento del programa premium antes de asumir que la membresía está generando una diferenciación económica significativa.

---

### 📱 Región y dispositivo

La asociación entre `region` y `tipo_dispositivo`, medida mediante **V de Cramér**, fue:

**V = 0,0124**

El resultado indica una asociación prácticamente nula entre ambas variables.

Por otro lado, el móvil representa aproximadamente **65 % del uso**, por lo que la optimización de la experiencia móvil aparece como una consideración importante independientemente de la región.

---

## 💡 Conclusiones de negocio

Los resultados sugieren que:

1. **La frecuencia de compra es el comportamiento más fuertemente asociado con el ingreso anual.**
2. **Las visitas mensuales tienen una asociación mucho menor**, por lo que el tráfico debe analizarse junto con la conversión.
3. **El gasto en publicidad dirigida presenta una asociación débil** con los ingresos.
4. **La satisfacción presenta una asociación prácticamente nula** con el ingreso anual en este dataset.
5. **La membresía premium no muestra una diferenciación clara** respecto al comportamiento de compra.
6. **El uso de dispositivos no presenta diferencias relevantes por región**, mientras que el móvil concentra la mayor parte del uso.

---

## ⚠️ Limitaciones

Este análisis presenta algunas limitaciones importantes:

* Las correlaciones encontradas **no demuestran causalidad**.
* La relación entre `compras_mes` e `ingreso_anual` es excepcionalmente alta y requiere validación.
* No se dispone de variables contextuales como precios promedio, estacionalidad, competencia o campañas específicas.
* Los datos representan una fotografía transversal y no permiten analizar evolución temporal.
* La variable de satisfacción puede no representar completamente la experiencia del cliente.
* La distribución de clientes premium está desbalanceada.
* La elevada relación entre compras e ingresos podría indicar redundancia entre las variables.

---

## 🚀 Próximos pasos

Como continuación del análisis se plantean:

* Auditar la relación entre `compras_mes` e `ingreso_anual`.
* Validar la calidad de la variable de satisfacción.
* Analizar la completitud y consistencia de las variables categóricas.
* Crear segmentos de clientes según frecuencia de compra.
* Aplicar **K-Means** para identificar perfiles de comportamiento.
* Analizar con mayor profundidad clientes premium vs. no premium.
* Evaluar relaciones categóricas mediante pruebas de **Chi-cuadrado**.
* Analizar diferencias de ingresos mediante **ANOVA**.

---

## 🛠️ Tecnologías utilizadas

* Python
* Pandas
* NumPy
* SciPy
* Matplotlib
* Seaborn
* Jupyter Notebook / Google Colab

---

## 📂 Estructura del repositorio

```text
novaretail-analysis/
│
├── notebooks/
│   └── novaretail_behavior_analysis.ipynb
│
├── README.md
│
└── ...
```

---

## ▶️ Cómo reproducir el análisis

1. Clona o descarga este repositorio.
2. Abre el notebook ubicado en `notebooks/`.
3. Ejecuta las celdas en orden.
4. Asegúrate de contar con las librerías utilizadas en el proyecto.
5. Verifica la ruta del dataset antes de ejecutar el análisis.

> El notebook original utiliza el dataset `novaretail_comportamiento_clientes_2024.csv`.

---

## 📓 Abrir en Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](URL_DEL_NOTEBOOK_EN_GITHUB)

También puedes abrir el notebook directamente desde GitHub y seleccionar **Open in Colab**.

---

## 👤 Proyecto

**Proyecto 7 — Explorando factores de comportamiento en NovaRetail+**

Análisis desarrollado como parte del proceso de formación en **Data Analytics**.

---

### 📌 Nota

Este proyecto tiene un propósito **exploratorio y analítico**. Los resultados deben interpretarse dentro del contexto y las limitaciones del dataset y no deben utilizarse para establecer relaciones causales sin análisis adicionales.
