# Proyecto Individual - Siniestros Viales 

## Lista de herramientas utilizadas

![Static Badge](https://img.shields.io/badge/PowerBI-gray?style=flat&logo=powerbi)
![Static Badge](https://img.shields.io/badge/Python-gray?style=flat&logo=python)
![Static Badge](https://img.shields.io/badge/-Pandas-gray?style=flat&logo=pandas)
![Static Badge](https://img.shields.io/badge/-Matplotlib-gray?style=flat&logo=matplotlib)
![Static Badge](https://img.shields.io/badge/-Seaborn-gray?style=flat&logo=seaborn)
![Static Badge](https://img.shields.io/badge/Visual_Studio_Code-gray?style=flat&logo=visual%20studio%20code&logoColor=white)

## Introducción

Los siniestros viales, también conocidos como accidentes de tránsito, representan un problema de salud pública de gran magnitud en Argentina, especialmente en ciudades densamente pobladas como Buenos Aires. Estos eventos, que involucran diversos tipos de vehículos, pueden tener consecuencias devastadoras, incluyendo daños materiales, lesiones graves y muertes. 

En este contexto, nos adentramos en el rol simulado de un Analista de datos que trabaja para el Observatorio de Movilidad y Seguridad Vial (OMSV) de la Ciudad de Buenos Aires, este nos solicita realizar un análisis de datos con el objetivo de identificar patrones y tendencias en los siniestros viales fatales ocurridos entre 2016 y 2021. Para ello, se nos ha proporcionado un conjunto de datos que contiene información detallada sobre los hechos y las víctimas.

Se busca obtener información valiosa que permita a las autoridades locales tomar medidas efectivas para reducir el número de víctimas fatales en siniestros viales y mejorar la seguridad vial en la ciudad.

## Objetivos del análisis:

- Identificar las principales causas de los siniestros viales fatales
* Analizar los perfiles de las víctimas más vulnerables.
+ Determinar los lugares de mayor concentración de siniestros
- Evaluar la efectividad de las medidas de seguridad vial implementadas

## Explicación del proyecto:

El conjunto de datos para el análisis de siniestros viales fatales en la Ciudad de Buenos Aires está compuesto por dos hojas de Excel:

#### HECHOS:

Contiene una fila por cada hecho de tránsito con un identificador único (ID).
Incluye variables temporales: fecha, año, mes, dia y hora del siniestro.
Variables espaciales: ubicación del hecho (Direccion, calle, cruce, comuna, coordenadas).
Variables sobre los participantes: tipo de vehículos involucrados, cantidad de victimas y trasnorte de las personas involucradas.

#### VÍCTIMAS:

Contiene una fila por cada víctima de un hecho de tránsito
Incluye variables sobre las víctimas: edad, sexo y rol en medio de transporte de desplazamiento (conductor, pasajero, peatón, ciclista).


## Proceso pre analisis:

Se inicio con la creacion de un <b>ambiente virtual</b> donde se podria hacer modificaciones en caso de ser necesarias para el manejo de las librerias. Se creo la carpeta <b>Database</b> para colocar los datasets dentro del archivo homicidios.xlsx y al momento de ser descargados pasa al formato .CSV para garantizar una lectura de la data con mas celeridad. 

## Proceso de ETL:
### Extracción:

Se extrajeron datos de 2 datasets:
- homicidios.xlsx - HECHOS.csv (link)
- homicidios.xlsx - VICTIMAS.csv (link)

Se instalo la librerias necesarias encontradas en el archivo de texto requirements.txt(link) lo que permitio un acceso rapido a la importacion de estas.

### Transformación y limpieza:

Se realizó un exploracion general de la data para identificar las columnas, la existencia de nulos (graficandolos para entender el alcance), reparando errores de nombramiento, datos diferentes a la mayoria, elementos y columnas de poca relevancia para el estudio, que luego fueron corregidos.

Se realizo un manejo previo de los nulo, imputando algunos entre conlumnas con relacion 

Se hizo un merge para combinar la información en 1 solo dataframe, y a este se le practicaron algunas tecnicas de trasformacion para manejar los datos <b>"SD"</b> en varias columnas. Ademas se crearon las columnas <b>"Rango_etario"</b> y <b>"Dia_nombre"</b>

### Carga:

Por ultimo con el dataframe preparado para el analisis si exporta con el nombre de <b>Data_siniestros.csv</b>

## Proceso de EDA:

### Preparación de datos:

Se carga el dataset desde el archivo <b>Data_siniestros.csv</b>, se chequean los datos y se eligen cuales columnas pasaran a formar el tipo "category", se pasan los datos de hora a tipo entero y se cambia la estructura de los datos de fecha a Año/Mes/Dia  

Se eliminaron registros duplicados, se observan datos nulos nuevos luego del merge.

### Análisis descriptivo y visual:

Se comienza a con las variables numericas llegando a las primeras concluciones.

Son mas comunes los accidente con 1 sola victima, siendo en muy pocas ocasiones mas de una y casi nunca mas de tres. El mayor indice de siniestros esta registrado entre los años 2016 y finales de 2019, posteriormente se refleja una reduccion presumiblemente debido al aislamiento que conllevo la pandemia del coronavirus entre el 2019 y 2021. Hay un alza de accidentes a mediados y finales de cada año que concuerda con las temporadas de vacaciones. Existe un incremento de accidentes en las horas de desplazamiento a las actividades laborales y estudiantiles de la mañana. La mayoria de las victimas estan ubicadas dentro de edades productivas comprendidas entre 20 y 40 años. 

Luego con el analisis de las variables categoricas fue posible corroborar lo que ya demostraba la describcion de las variables numericas para asi crear un perfil de las victimas y la situcion de los siniestros.

Perfil de elementos sobresalientes en los sucesos 

  * Tipo calle con mas fluencia de accidentes :<b> Avenida </b> 
  * Comuna con mas influencia:<b> Comuna '1'</b>
  * Rol: las victimas son <b>Conductores</b>
  * Victima: Conductores de <b>motos</b>
  * Acusado: Conductores de <b>autos</b>
  * Sexo: <b>masculino</b>
  * Rango etario de las victimas: <b>Entre 21 y 40 años</b>
  * Meses:<b>Los meses vacacionales </b>
  * Dias con mas fluencia de accidentes : <b>Martes y sabado</b> y con fechas <b> entre el 15 y 20 </b> de cada mes  

### Conclusiones:

El análisis de los datos ha revelado información valiosa sobre los patrones y tendencias La información obtenida puede ser utilizada por las autoridades locales para diseñar e implementar políticas públicas efectivas para la reducción de estos eventos.
Se recomienda realizar un análisis más profundo para identificar las causas específicas de los siniestros viales fatales en las avenidas y entre los hombres jóvenes.

### Recomendaciones:

- Implementar una mejor señalización en las avenidas.
- Reducir la velocidad vehicular en las zonas con mayor concentración de accidentes.
- Realizar campañas de sensibilización sobre seguridad vial dirigidas a los hombres jóvenes.
- Continuar recopilando y analizando datos sobre siniestros viales fatales para mejorar la comprensión del problema y la efectividad de las intervenciones.

