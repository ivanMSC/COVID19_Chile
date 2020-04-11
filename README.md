# Panel Interactivo
Para ver el Panel Interactivo visite https://tiny.cc/covid19chile

# Base de datos del COVID-19 en toda Latinoamérica
En este [repo](https://github.com/DataScienceResearchPeru/covid-19_latinoamerica) estamos trabajando para la recopilación de la información de toda latinoamérica ~~ya que nuestros gobiernos son en su grueso ineptos y tenemos que hacer todo nosotros mismos~~. 
Yo estoy a cargo de la data de Chile y del [panel](https://datastudio.google.com/u/2/reporting/9b824956-4055-46da-8c40-0d46ded5ffba/page/QkcKB) que muestra la evolución de cada país por estado/provincia/región/departamento. Se necesitan manos, y estamos recibiendo gente con ganas de buscar la información.

# Base de datos nivel regional MinSal.
La base de datos original de este repositorio, actualizada hasta el 29-03-2020 ha sido movida a la carpeta `old` y no seguira su mantención. Esto pues, su contenido ya no tenía sentido.
La base nueva, archivo con el mismo nombre `covid19_chile.csv`, en la misma ubicación tiene ahora una nueva estructura:
* `Fecha`
* `Region`
* `Nuevo Confirmado`
* `Nuevo Muerte`
* `Nuevo Recuperado`
* `Acum Confirmado`
* `Acum Muerte`
* `Acum Recuperado`

Los nombres de los campos no necesitan explicación. El campo `Region` puede tomar el valor `No informado` para incluir los casos recuperados que el gobierno se niega a entregar desglosados.

# Base de datos nivel Comunal

## Datos Históricos y actualizaciones diarias
En el archivo `historial_comunas.csv` encontrará una serie de datos de los casos confirmados acumulados para cada region desglosados por comuna. Los historiales se encuentran completos para las regiones de: Arica y Parinacota, Tarapacá, Antofagasta, Atacama, Coquimbo, Valparaíso*, O'Higgins, Los Lagos, Aysén y Magallanes. Para la región metropolitana, no existen datos históricos accesibles. Las demás regiones, ha sido difícil encontrar fuentes para datos anteriores al 29 de marzo, por lo que no poseen datos diarios antes de esa fecha. Si usted posee la información, le agradeceré compartirla para incluirla en este repositorio!

Los datos son obtenidos día a día desde comunicados oficiales de los gobiernos y organismos regionales, por lo que pueden tener un corte horario distinto al del ministerio de Salud o por existir algunos casos que en el día de reporte se encuentran en investigación de comuna.

Los campos son:
* `Fecha` en formato `dd-mm-yyyy`
* `CUT` Código único territorial. Códigos especiales: `5999` = `Barco Isabela Island` en Valparaíso y `10999` = `Barco Silver Explorer` en Los Lagos. 
* `Region` Código ISO 3166-2.
* `Comuna`
* `Confirmados Acumulados`

Si alguna comuna no está es porque no ha reportado casos a la fecha de actualización. En la RM, se reportan los datos solo para los días lunes, miércoles y viernes desde el 30-mar-2020; y en los demás días no existe data.

*Los números de la región de Valparaíso pueden ser no muy confiables, pues el Seremi ha reportado solo los casos nuevos y no los acumulados día a día, por lo que pueden haber discrepancias al totalizar la cuenta respecto de otras fuentes.

## Datos MinSal Informe Epidemiológico
En el archivo `covid19_comunas.csv` encontrará la serie de tiempo de los casos confirmados por comuna, obtenida del informe epidemiológico que sube el ministerio de salud a contar del 31-mar-2020.

# Ministerio de Ciencia

Al parecer nos han escuchado. [El Ministerio de Ciencia tiene un repo](https://github.com/MinCiencia/Datos-COVID19). Ahí suben unos CSV con casos por region y comuna. Lamentablemente, la información no es más de la que ya tenemos. Aunque preferiría pensar que es porque están recién comenzando. Tiene algunos problemas, por ejemplo, no reportan el número de casos por cumuna si el número de casos es menor a 4 (lo que hago yo para rellenar la información es multiplicar la tasa por la población y redondear); no entregan el número de recuperados y muertos por comuna, etc. Mientras no se solucionen esos problemas, seguiré manteniendo el archivo en la medida que se publique más información.



## Conectarse
Para descargar o conectarse a la base de datos directamente, usar la dirección pública https://raw.githubusercontent.com/ivanMSC/COVID19_Chile/master/covid19_chile.csv
o https://raw.githubusercontent.com/ivanMSC/COVID19_Chile/master/covid19_comunas.csv
