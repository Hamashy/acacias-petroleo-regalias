<div align="center">

# ¿Acacías vive del petróleo?

**Regalías vs. desarrollo en un municipio petrolero de Colombia · 2012–2026**

Un proyecto de análisis de datos de **[Carlos Andrés Morales Rojas](https://www.linkedin.com/in/carloscamr/)**

![Python](https://img.shields.io/badge/Python-1D1D1F?style=flat-square&logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-1D1D1F?style=flat-square&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-1D1D1F?style=flat-square&logo=jupyter&logoColor=white)
![Datos abiertos](https://img.shields.io/badge/Datos_abiertos-Colombia-0071E3?style=flat-square)

</div>

<br>

<p align="center"><img src="figuras/laminas/lamina_01.png" alt="¿Acacías vive del petróleo? Cifras clave del proyecto" width="620"></p>

<br>

Acacías, en el Meta, produce cerca de **100.000 barriles de petróleo al día**. Este proyecto cruza seis fuentes de datos públicos para responder una pregunta sencilla: **¿esa riqueza se tradujo en una mejor vida para sus habitantes?**

<br>

## La historia en seis preguntas

### 1 · ¿Cuánto petróleo produce Acacías?

Producción fiscalizada que reporta la Agencia Nacional de Hidrocarburos, campo por campo. Un mismo volumen aparece repetido por cada régimen de regalías, así que antes de sumar se quitaron esas repeticiones; sin ese paso, la producción del Meta quedaba inflada en un 6%.

<p align="center"><img src="figuras/laminas/lamina_02.png" alt="Un gigante petrolero" width="620"></p>

### 2 · ¿Cuánto de esa riqueza le llega al municipio?

Aquí se cruzan dos fuentes que miden cosas distintas: la ANH calcula las regalías que genera el petróleo extraído en Acacías, y SICODIS registra la plata que efectivamente llega a la alcaldía. Todo está en pesos de 2025 para poder comparar años.

<p align="center"><img src="figuras/laminas/lamina_03.png" alt="Genera mucho, recibe poco" width="620"></p>

### 3 · ¿En qué se invierte lo que llega?

Proyectos de MapaInversiones cuya entidad responsable es la alcaldía y que se financian con regalías. Solo se cuentan los aprobados (terminados, en ejecución o viables), no los que se quedaron en formulación.

<p align="center"><img src="figuras/laminas/lamina_04.png" alt="Lo que llega se vuelve cemento" width="620"></p>

### 4 · ¿Se nota en la vida de la gente?

Ocho indicadores de TerriData, con el último dato disponible de Acacías, el Meta y Colombia. En azul, donde Acacías está mejor que ambos; en naranja, donde está peor.

<p align="center"><img src="figuras/laminas/lamina_05.png" alt="Mejor que el promedio, salvo en la universidad" width="620"></p>

### 5 · ¿Qué pasó con la pobreza?

La pobreza multidimensional por municipio solo se mide con los censos, por eso hay dos puntos: 2005 y 2018. Para comparar, aparecen los otros municipios petroleros del Meta, la capital, el departamento y el país.

<p align="center"><img src="figuras/laminas/lamina_06.png" alt="La pobreza cayó a menos de la mitad" width="620"></p>

### 6 · ¿Cómo contrata la alcaldía?

Contratos de SECOP II firmados mes a mes desde 2021. La Ley de Garantías prohíbe la contratación directa en los cuatro meses antes de las elecciones presidenciales. Los nombres y documentos de las personas contratadas se anonimizaron.

<p align="center"><img src="figuras/laminas/lamina_07.png" alt="Enero se dispara antes de las elecciones" width="620"></p>

<br>

## ¿Y entonces?

<p align="center"><img src="figuras/laminas/lamina_08.png" alt="Conclusiones del proyecto" width="620"></p>

Estos datos describen lo que pasó, pero no prueban que las regalías hayan causado las mejoras: el paso natural es comparar a Acacías con municipios parecidos que no tienen petróleo.

<br>

## Cómo se hizo

<details>
<summary><b>Fuentes de datos</b></summary>
<br>

| Fuente | Qué aporta |
|---|---|
| **ANH** | Producción de petróleo y regalías generadas por campo y municipio |
| **DNP · SICODIS** | Regalías que efectivamente recibe la alcaldía |
| **DNP · MapaInversiones** | Proyectos financiados con regalías |
| **DNP · TerriData** | Indicadores de educación, salud, servicios, seguridad y pobreza |
| **SECOP II** | Contratos firmados por la alcaldía |
| **DANE** | IPC, para expresar todo en pesos de 2025 |

El detalle de filtros, archivos y fechas de descarga está en [`fuentes.md`](fuentes.md).

</details>

<details>
<summary><b>Pipeline de notebooks</b></summary>
<br>

| Notebook | Qué hace |
|---|---|
| [`01_limpieza_anh`](notebooks/01_limpieza_anh.ipynb) | Une 15 archivos anuales de la ANH y corrige la producción duplicada por régimen de regalías |
| [`02_limpieza_sicodis`](notebooks/02_limpieza_sicodis.ipynb) | Lee encabezados de dos filas y formatos que cambian entre bienios |
| [`03_ipc_pesos_constantes`](notebooks/03_ipc_pesos_constantes.ipynb) | Lleva todos los valores a pesos de 2025 |
| [`04_proyectos_inversion`](notebooks/04_proyectos_inversion.ipynb) | Clasifica la inversión por sector y detecta proyectos para seguimiento |
| [`05_terridata_indicadores`](notebooks/05_terridata_indicadores.ipynb) | Filtra archivos de hasta 1 GB por pedazos y compara indicadores |
| [`06_secop_contratacion`](notebooks/06_secop_contratacion.ipynb) | Analiza modalidades, Ley de Garantías y concentración de proveedores, con datos personales anonimizados |
| [`07_analisis_final`](notebooks/07_analisis_final.ipynb) | Arma la historia y genera las gráficas de análisis en modo claro y oscuro |

Las láminas del README (`figuras/laminas/`) son un rediseño de presentación de esas gráficas, en formato 1200 × 1500 px, con las mismas cifras.

</details>

<details>
<summary><b>Validaciones</b></summary>
<br>

| Qué se validó | Resultado |
|---|---|
| Producción de Chichimene, julio 2025 | 37.227 barriles/día, igual a la cifra publicada por la ANH |
| Recaudo de Acacías 2013-2014 | Coincide al peso con el total del reporte de SICODIS |
| Inflación de 2022 | 13,12%, igual a la cifra oficial del DANE |

</details>

<details>
<summary><b>Limitaciones</b></summary>
<br>

- **Correlación no es causalidad.** Que un indicador mejore mientras llegan regalías no prueba que las regalías lo causaron.
- **"Recibidas" incluye solo las Asignaciones Directas.** No se cuantificó la inversión de la Gobernación dentro del municipio.
- **Algunos indicadores cambian de metodología** (vacunación en 2021, mortalidad infantil en 2017).
- **SECOP II cubre a la alcaldía solo desde 2021.**
- **Avances físicos en 0%** en MapaInversiones parecen falta de reporte: el cruce con SECOP muestra contratos ejecutados y prorrogados.

</details>

<details>
<summary><b>Cómo reproducirlo</b></summary>
<br>

```bash
git clone https://github.com/Hamashy/acacias-petroleo-regalias.git
cd acacias-petroleo-regalias
pip install -r requirements.txt
```

1. Descarga los datos crudos siguiendo [`fuentes.md`](fuentes.md) y guárdalos en `data/`. No se incluyen en el repositorio por su tamaño.
2. Corre los notebooks en orden, del `01` al `07`, desde la carpeta `notebooks/`.

</details>

<br>

## Autoría

Este proyecto es de **autoría propia de Carlos Andrés Morales Rojas**: la pregunta de investigación, la recolección de datos, la limpieza, el análisis y las visualizaciones.

<div align="center">

<br>

**Carlos Andrés Morales Rojas**

[LinkedIn](https://www.linkedin.com/in/carloscamr/) · [GitHub](https://github.com/Hamashy)

<sub>© 2026 Carlos Andrés Morales Rojas · Datos públicos de entidades del Estado colombiano</sub>

</div>
