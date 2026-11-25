# Fuentes de datos

Todas las descargas se hicieron el **24 de noviembre de 2026**. Todos los datos son públicos.

## 1. ANH: Producción y Regalías por Campo

- **Entidad:** Agencia Nacional de Hidrocarburos (ANH)
- **Sitio:** https://www.anh.gov.co → consulta *Producción y Regalías x Campo*
- **Filtros:** Departamento = META · Año = 2012 a 2026 (un archivo por año) · Trimestre = Todos · Mes = todos · Campo = vacío (todos)
- **Archivos:** `data/anh/anonimus_ProduccionyRegaliasxCampo*.xlsx` (15 archivos, uno por año)
- **Contenido:** producción fiscalizada mensual (barriles de petróleo y Kpc de gas) y regalías liquidadas en COP, por municipio, contrato, campo y régimen de regalías
- **Notas:** 2026 llega hasta junio. Los datos están en la segunda hoja de cada Excel.
- **Usado en:** notebook 01

## 2. SICODIS: Recaudo de Asignaciones Directas

- **Entidad:** Departamento Nacional de Planeación (DNP)
- **Sitio:** https://sicodis.dnp.gov.co → SGR → *Resumen PBC vs Recaudo – Asignaciones Directas*
- **Filtros:** Entidad = Acacías (Meta) · Vigencias = 2013-2014 a 2025-2026 (un archivo por bienio)
- **Archivos:** `data/sicodis/ResumenPBCvsRecaudo*.xlsx` (7 archivos)
- **Contenido:** Plan Bienal de Caja (PBC) y recaudo mensual de Asignaciones Directas. La hoja de detalle trae todas las entidades del país.
- **Notas:** pesos corrientes. Fecha de corte del recaudo: 31/10/2026. La carpeta `data/sgr recaudo directa` es una copia duplicada del mismo reporte y no se usa.
- **Usado en:** notebook 02

## 3. SICODIS: Plan de Recursos

- **Entidad:** Departamento Nacional de Planeación (DNP)
- **Sitio:** https://sicodis.dnp.gov.co → SGR → *Plan de Recursos*
- **Filtros:** Departamento = Meta · Beneficiario = Acacías · Vigencias = 2013-2022 a 2025-2034 (un archivo por vigencia)
- **Archivos:** `data/sgr plan de recursos/DetallePlanRecursos*.xlsx` (7 archivos)
- **Contenido:** proyección a 10 años de los recursos del SGR asignados a Acacías
- **Notas:** se usan solo los dos primeros años de cada plan, que corresponden al bienio vigente.
- **Usado en:** notebook 02

## 4. MapaInversiones: Proyectos de inversión

- **Entidad:** Departamento Nacional de Planeación (DNP)
- **Reporte Datos Básicos:** https://mapainversiones.dnp.gov.co/reportes/datosbasicos
  - **Filtros:** Estados = Todos · Sector = Todos · Entidad Responsable = Acacías, Meta · Vigencias = Todos
  - **Archivo:** `data/proyectos_sgr/Reporte_Reporte_ProyectosDatosBásicos.xlsx`
- **Reporte Localización:** https://mapainversiones.dnp.gov.co/reportes/datoslocalizacion
  - **Filtros:** Municipio = Acacías (Meta)
  - **Archivo:** `data/proyectos_sgr/Reporte_DatosLocalizacion.csv`
- **Contenido:** proyectos de inversión pública con BPIN, sector, estado, valores y avance físico y financiero
- **Notas:** la descarga se hizo durante un mantenimiento de la plataforma; el DNP avisaba de posibles inconsistencias mientras sincronizaba las bases. Valores en pesos corrientes.
- **Usado en:** notebook 04

## 5. TerriData: Indicadores territoriales

- **Entidad:** Departamento Nacional de Planeación (DNP)
- **Sitio:** https://terridata.dnp.gov.co/index-app.html#/descargas → *Descarga por dimensión* (formato TXT)
- **Archivos:** `data/terridata/TerriData_Dim*.txt`

| Archivo | Dimensión |
|---|---|
| Dim2 | Demografía y población |
| Dim3 | Vivienda y acceso a servicios públicos |
| Dim4 | Educación |
| Dim5 | Salud |
| Dim6 | Convivencia y seguridad ciudadana |
| Dim7 | Finanzas públicas |
| Dim8 | Medición de desempeño municipal |
| Dim12 | Economía |
| Dim14 | Pobreza |

- **Contenido:** indicadores de todos los municipios del país, separados por `|`, con números en formato colombiano (punto de miles, coma decimal)
- **Notas:** el notebook 05 filtra Meta (código 50) y Colombia (código 01) y guarda `data processed/terridata_meta_colombia.csv`.
- **Usado en:** notebook 05

## 6. SECOP II: Contratos Electrónicos

- **Entidad:** Colombia Compra Eficiente
- **Sitio:** https://www.datos.gov.co → dataset *SECOP II - Contratos Electrónicos*
- **Filtros:** Departamento contiene "Meta" **y** Ciudad contiene "Acac"
- **Archivo:** `data/secop contratos/SECOP_II_-_Contratos_Electrónicos_20261124.csv` (9.861 contratos)
- **Contenido:** contratos de las entidades con sede en Acacías (alcaldía, hospital, tránsito, cárcel, concejo, personería)
- **Notas:** la alcaldía aparece en SECOP II desde 2021. No se descargó SECOP I (2013-2020). El archivo trae datos personales; el notebook 06 los descarta y anonimiza a las personas naturales.
- **Usado en:** notebook 06

## 7. DANE: Índice de Precios al Consumidor (IPC)

- **Entidad:** Departamento Administrativo Nacional de Estadística (DANE)
- **Sitio:** https://www.dane.gov.co → Estadísticas por tema → Precios y costos → Índice de Precios al Consumidor (IPC) → *Índices - series de empalme - octubre 2026*
- **Archivo:** `data/ipc/anex-IPC-Indices-oct2026.xlsx`
- **Contenido:** índice mensual del IPC total nacional, enero 2003 a octubre 2026 (base diciembre 2018 = 100)
- **Usado en:** notebook 03, para pasar todo a pesos constantes de 2025

## Cifras usadas para validar

| Validación | Valor | Fuente |
|---|---|---|
| Producción del campo Chichimene, julio 2025 | 37.227 barriles/día | ANH, reportado por Portafolio |
| Inflación anual 2022 (dic-dic) | 13,12% | DANE |
| Ley de Garantías 2026 | 31 de enero a 21 de junio de 2026 | Ley 996 de 2005, art. 33 |
