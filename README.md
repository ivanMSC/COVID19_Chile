## FIN DE SOPORTE: 19 JUNIO 2022

## Actualización instantánea
Las actualizaciones de los datos regionales son instantáneas y autónomas. Hice un robot que está funcionando en un servidor de Google que mira la pagína del gobierno todos los días a partir de las 9 am, cada 1 minuto y verifica si hay datos nuevos. Si los encuentra, los sube a GitHub. El bot va a seguir corriendo incluso si me muero. Si hay un error en la data, contácteme.


## Panel Interactivo
Para ver el Panel Interactivo visite https://tiny.cc/covid19chile

## Índice
- [Base de datos nivel Comunal](#base-de-datos-nivel-comunal)
  * [Datos Históricos y actualizaciones diarias](#datos-históricos-y-actualizaciones-diarias)
  * [Datos MinSal Informe Epidemiológico](#datos-minsal-informe-epidemiológico)
- [Base de datos nivel regional MinSal.](#base-de-datos-nivel-regional-minsal)
- [Ministerio de Ciencia](#ministerio-de-ciencia)
- [Base de datos del COVID-19 en toda Latinoamérica](#base-de-datos-del-covid-19-en-toda-latinoamérica)
- [Carpeta Utils y Mapa de Chile](#carpeta-utils-y-mapa-de-chile)
- [Conectarse](#conectarse)

# Base de datos nivel Comunal

## Datos Históricos y actualizaciones diarias
En el archivo `historial_comunas.csv` ([link directo](https://raw.githubusercontent.com/ivanMSC/COVID19_Chile/master/historial_comunas.csv)) encontrará una serie de datos de los casos confirmados acumulados para cada region desglosados por comuna. Los historiales se encuentran completos para las regiones de: Arica y Parinacota, Tarapacá, Antofagasta, Atacama, Coquimbo, Valparaíso, O'Higgins, Ñuble, Biobío, Los Ríos, Los Lagos, Aysén y Magallanes. Para la región metropolitana, no existen datos históricos accesibles. Las demás regiones (Maule y Araucanía) ha sido difícil encontrar fuentes para datos anteriores al 29 de marzo, por lo que hasta el momento, no tengo datos diarios antes de esa fecha. Si usted posee la información o alguna fuente, le agradeceré compartirla para incluir los datos en este repositorio!

Los datos son obtenidos día a día desde comunicados oficiales de los gobiernos y organismos regionales (SEREMI o intendencias), por lo que pueden discrepar del total general regional entregado por MinSal. Esto puede ser por tener un corte horario distinto o por existir casos que en el día de reporte se encuentran en investigación de comuna de origen que son omitidos.

### Regiones por completar 
| Región | Datos desde |
| ------------- | ------------- |
| Metropolitana  | 30-mar-2020 y solo algunos dias  |
| Maule  | 29-mar-2020  |
| Araucanía  | 23-mar-2020  |

Las demás regiones están completas.

### Fuentes
El proceso de extracción de datos está automatizado, mientras que la verificación es semi manual. 
Para cada región, se verficia  las fuentes que se listan a continuación, diariamente y se obtienen los datos del total acumulado. 
Para ello se recurre a, por ejemplo, un API de OCR provisto por Google Drive, scraping de dashboards implementado en Google Apps Script, etc.

Para scrapear Twitter, no tengo un key del API, pero lo bypasseo usando https://nitter.net/ (dios lo guarde y lo proteja)

Todo esto está alojado en un proyecto de Google Apps Script y funciona en servidores de Google, siendo los resultados centralizados en un Google Sheets (no regrets).
Absolutamente gratis.

Todas las fuentes son publicas y pueden ser visitadas a continuación:

|Región|Fuentes|
|-------|-------|
|Arica y Parinacota|[Gore](https://twitter.com/goredearica), Reportes Minsal|
|Tarapacá|[Seremi](https://twitter.com/SeremiSalud_I), [Gore](https://twitter.com/Gore_Tarapaca)|
|Antofagasta|[Gore](https://twitter.com/GOREAntofagasta), [Dashboard oficial](https://experience.arcgis.com/experience/13813048c0d54a61bc53d536225d5e28/)
|Atacama|[Seremi](https://twitter.com/SeremiSalud3)|
|Coquimbo|[Gore](https://twitter.com/gorecoquimbo), [Seremi](https://twitter.com/SeremiSalud_Coq), [ULS](https://bigdatauls.userena.cl/salud/covid-19/region-coquimbo/)|
|Valparaíso|[Seremi](https://seremi5.redsalud.gob.cl/reporte-regional), [Seremi Twitter](https://twitter.com/SaludSsrv)|
|O'Higgins|[Municipalidad de Rancagua](https://twitter.com/munirancagua),[Gore](http://www.goreohiggins.cl/noticias/noticias-gore/108-covid-19-informe-diario)|
|Maule|[Seremi](https://twitter.com/SeremiSaludM), [SSMaule](https://twitter.com/SSMaule)|
|Ñuble|[Seremi](https://www.seremidesaludnuble.cl/comunicado-regional-covid-19/), [Chillan Online](http://www.chillanonline.cl/V5/), [Ñuble Online](https://twitter.com/NUBLEONLINE_)|
|Biobío|[Seremi](http://www.seremidesaludbiobio.cl/sd/web/#), [Seremi Facebook](https://www.facebook.com/seremisalud.biobio/)|
|Araucanía|[Seremi](https://seremi9.redsalud.gob.cl/9370-2/)|
|Los Ríos|[Seremi](https://seremi14.redsalud.gob.cl/), [Dashboard Oficial](https://www.canva.com/design/DAD6TwPrraQ/0w6qmDIE9COQP9cUOSek6w/view?utm_content=DAD6TwPrraQ&utm_campaign=designshare&utm_medium=link&utm_source=publishsharelink)|
|Los Lagos|[Seremi](https://seremi10.redsalud.gob.cl/17466-2/)|
|Aysén|[Seremi](https://seremi11.redsalud.gob.cl/coronavirus/)|
|Magallanes|[Dashboard oficial](https://contingencia-coronavirus-snit-magallanes.hub.arcgis.com), [Seremi](https://seremi12.redsalud.gob.cl/), [Intendencia](https://twitter.com/IntendenciaM)|

### Campos del archivo
* `Fecha` en formato `dd-mm-yyyy`
* `CUT` Código único territorial. Códigos especiales: `5999` = `Barco Isabela Island` en Valparaíso y `10999` = `Barco Silver Explorer` en Los Lagos. 
* `Region` Código ISO 3166-2.
* `Comuna`
* `Confirmados Acumulados`
* `Nuevos Confirmados`

Si alguna comuna no está es porque no ha reportado casos a la fecha de actualización. En la RM, se reportan los datos solo los días del informe epidemiológico; y en los demás días no existe data.

## Datos MinSal Informe Epidemiológico
En el archivo `covid19_comunas_informeEpidemiologico.csv` ([link directo](https://raw.githubusercontent.com/ivanMSC/COVID19_Chile/master/covid19_comunas_informeEpidemiologico.csv)) encontrará la serie de tiempo de los casos confirmados por comuna, obtenida del informe epidemiológico que sube el ministerio de salud a contar del 31-mar-2020.

# Base de datos nivel regional MinSal.
La base de datos original de este repositorio, actualizada hasta el 29-03-2020 ha sido movida a la carpeta `old` y no seguira su mantención. Esto pues, su contenido ya no tenía sentido.
La base nueva, archivo con el mismo nombre `covid19_chile.csv` ([link directo](https://raw.githubusercontent.com/ivanMSC/COVID19_Chile/master/covid19_chile.csv)), en la misma ubicación tiene ahora una nueva estructura:
* `Fecha`
* `Region`
* `Nuevo Confirmado`
* `Nuevo Muerte`
* `Nuevo Recuperado`
* `Acum Confirmado`
* `Acum Muerte`
* `Acum Recuperado`
* `Casos UCI`

Los nombres de los campos no necesitan explicación. El campo `Region` puede tomar el valor `No informado` para incluir los casos recuperados que el gobierno se niega a entregar desglosados.

# Ministerio de Ciencia

Para información y data oficial visite el repositorio del [Ministerio de Ciencia](https://github.com/MinCiencia/Datos-COVID19).

# Base de datos del COVID-19 en toda Latinoamérica
En este [repo](https://github.com/DataScienceResearchPeru/covid-19_latinoamerica) estamos trabajando para la recopilación de la información de toda latinoamérica. 
Yo estoy a cargo de la data de Chile y del [panel](https://datastudio.google.com/u/2/reporting/9b824956-4055-46da-8c40-0d46ded5ffba/page/QkcKB) que muestra la evolución de cada país por estado/provincia/región/departamento. Se necesitan manos, y estamos recibiendo gente con ganas de buscar la información.

# Carpeta Utils y Mapa de Chile
En esta carpeta encontrará tablas relacionadas a países, regiones de Chile y Comunas de Chile. Además de un mapa TopoJSON de Chile subdividido en Comunas, ideal para la creación de dashboards. Cada polígono del mapa tiene un ID que es igual al CUT de la Comuna.

# Conectarse
Para descargar o conectarse a la base de datos directamente, usar la dirección pública https://raw.githubusercontent.com/ivanMSC/COVID19_Chile/master/covid19_chile.csv
https://raw.githubusercontent.com/ivanMSC/COVID19_Chile/master/covid19_comunas_informeEpidemiologico.csv
https://raw.githubusercontent.com/ivanMSC/COVID19_Chile/master/historial_comunas.csv
