## Panel Interactivo
Para ver el Panel Interactivo visite https://tiny.cc/covid19chile

# ANUNCIO 1: Base de datos ahora con nuevo formato.
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

# ANUNCIO 2 Base de datos de comunas
Tenemos datos por comuna. En el archivo `covid19_comunas.csv` encontrará la serie de tiempo de los casos confirmados por comuna, obtenida del informe epidemiológico que sube el ministerio de salud a contar del 31-mar-2020. ~~Qué tienen en la cabeza? A quién le sirve un PDF? Qué les cuesta subir un CSV? Si alguien del ministerio está leyendo esto, en realidad no me cuesta mucho scrapear un pdf con algo de kung fu, pero sería lo apropiado que subieran un csv. Mientras tanto, intentaré mantener el archivo actualizado en la medida que aparezcan más datos.~~ 

Al parecer nos han escuchado. [El Ministerio de Ciencia tiene un repo](https://github.com/MinCiencia/Datos-COVID19). Ahí suben unos CSV con casos por region y comuna. Lamentablemente, la información no es más de la que ya tenemos. Aunque preferiría pensar que es porque están recién comenzando. Tiene algunos problemas, por ejemplo, no reportan el número de casos por cumuna si el número de casos es menor a 4 (lo que hago yo para rellenar la información es multiplicar la tasa por la población y redondear); no entregan el número de recuperados y muertos por comuna, etc. Mientras no se solucionen esos problemas, seguiré manteniendo el archivo en la medida que se publique más información.

## Conectarse
Para descargar o conectarse a la base de datos directamente, usar la dirección pública https://raw.githubusercontent.com/ivanMSC/COVID19_Chile/master/covid19_chile.csv
o https://raw.githubusercontent.com/ivanMSC/COVID19_Chile/master/covid19_comunas.csv
