# Práctica hidrología | Curso: G1966 - Hidrología
Este repositorio contiene la guía y notebooks para seguir el ejemplo de clase sobre la cuenca del [río Asón](https://earth.google.com/web/@43.33331797,-3.45281217,275.83860964a,24356.42170509d,35y,164.10293665h,59.8563698t,-0r/data=MikKJwolCiExUjRkU040QVJxYWRsUW0wbG5teFRfX3JmX004M2dnd1YgAToDCgEw). De este modo se espera que el material depositado aquí sirva de apoyo para el desarrollo de la práctica sobre la cuenca seleccionada por cada estudiante.

La práctica se divide en módulos durante los cuales se utilizarán diferentes softwares y rutinas para generar y procesar todos los datos y ficheros necesario para la consecución exitosa de la práctica.
 A continuación, se presenta una pequeña descripción de cada módulo y el enlace a su respectivo subdirectorio que contiene los notebooks, ficheros e instrucciones relacionados al módulo:

 ## Módulo 1: Caracterización hidrológica de la cuenca (Parte 1)
 A lo largo de este módulo se escogerá el cauce a estudiar con ayuda del [visor SIG](https://sig.mapama.gob.es/redes-seguimiento/) de las Redes de Seguimiento del estado e Información Hidrológica. Luego, se obtendrán los ficheros vectoriales que servirán de guía (máscara) para descargar las Hojas cartográficas del Modelo digital del terreno (MDT) desde el [Centro de Descargas](https://centrodedescargas.cnig.es/CentroDescargas/index.jsp) del Centro Nacional de Información Geográfica; los ficheros vectoriales se obtendrán de la base de datos global de información hidrológica [HydroSHEDS](https://www.hydrosheds.org/). De este modo, con el software [ArcGIS Pro](https://www.esri.com/es-es/arcgis/products/arcgis-pro/overview) se preparará el MDT para ser utilizado como fichero de entrada en [HEC-HMS](https://www.hec.usace.army.mil/software/hec-hms/). Con el sofrware HEC-HMS se realizará la delineación y caracterización inicial de la cuenca y subcuencas correspondientes al cauce elegido.
 > La guía y ficheros de este módulo se encuentran [**aquí**]()

## Módulo 2: Caracterización hidrológica de la cuenca (Parte 2)
Este módulo gira en torno a la determinación del número de curva de la cuenca y subcuencas de trabajo. Primero, se obtendrán los mapas de mapas de entrada para el cálculo del número de curva (mapa de pendientes, mapa de tipo de cobertura, mapa grupo hidrológico del suelo). El mapa de pendientes se generará con base en el mismo MDT que se utilizó para delinear la cuenca en HEC-HMS, el mapa de tipo de cobertura se descargará del Centro de de Descargas del Centro Nacional de Información Geográfica y el mapa del grupo hidrológico del suelo se obtendrá con base en la base de datos global de suelos [SoilGrids](https://soilgrids.org/) y el notebook [***01_GrupoHidro***](). (También es posible que no sea necesario determinar un mapa del grupo hidrológico del suelo si se observa que toda la cuenca se encuentra sobre el área marcada para un mismo grupo hidrológico del suelo en el visor GIS [SIGCAR](https://beta.sigcar.es/sigc.php)). 

Segundo, se creará un mapa con con los id de referencia para cada combinación de tipo de cobertura, grupo hidrológico del suelo y pendiente de modo que se pueda relacionar con la ___Tabla 2.4.___ _GRUPOS HIDROLÓGICOS DE SUELO A EFECTOS DE LA DETERMINACIÓN DEL VALOR
INICIAL DEL UMBRAL DE ESCORRENTÍA__ de la [Norma 5.2-IC](https://www.boe.es/boe/dias/2016/03/10/pdfs/BOE-A-2016-2405.pdf) (Ministerio de Fomento, 2016, España). Por último, se determinará el número de curva medio de la cuenca y cada subcuenca con el notebook [***02_CN***]().
 > La guía y ficheros de este módulo se encuentran [**aquí**]()

## Módulo 3: Caracterización hidrológica de la cuenca (Parte 3)
En este módulo se obtendrán y prepararán las series temporales con la información de precipitación de la cuenca. Esta información se extraerá del conjunto de datos [Spain02](https://www.aemet.es/es/serviciosclimaticos/cambio_climat/datos_diarios?w=2&w2=1) elaborado conjuntamente por AEMET y el grupo de [Meteorología de Santander](https://github.com/SantanderMetGroup), para esto se utilizará el notebook [***03_SPAIN02***](). Así mismo, con estas series se construirán las curvas IDF y los hietogramas de tormenta para cada punto de información con los notebook [***04_CurvasIDF***]() y [***05_Hietograma***](), respectivamente. 
 > La guía y ficheros de este módulo se encuentran [**aquí**]()

## Módulo 4: Caracterización hidrológica de la cuenca (Parte 4)
Siguiendo los notebooks [***06_ThiessenPoly***]() y [***07_Hipsométrico***]() se determinará la precipitación media anual para la cuenca y cada subcuenca según el método de los polígonos de Thiessen y el método hipsométrico, respectivamente. Por otra parte, se seguirá el notebook [***08_Clark_Muskingum***]() para contruir el hidrograma unitario de Clark y estimar los párametros K y X de Muskingum para definir el tránsito del hidrograma correspondiente a un tramo aforado de la red de cauces de la cuenca. Para esto, será necesario descargar desde el anuario [aforos](https://ceh.cedex.es/anuarioaforos/demarcaciones.asp) la información de caudal diario medida en una estación de aforo de la cuenca
 > La guía y ficheros de este módulo se encuentran [**aquí**]()

## Módulo 5: Generación de hidrogramas de respuesta con Hec-HMS
Este módulo se compone de dos partes: 
- En la primera parte se realizará una calibración de los párametros K y X  correspondientes al método de enrutado de Muskingum para los tramos principales de la cuenca definidos en HEC-HMS. Para ello se configurará el modelo de acuerdo a la caracterización de la cuenca realizada en los módulos anteriores y se utilizarán los datos de caudal diario descargados en la estación de aforo para la calibración.
- En la segunda parte, se utilizará el modelo hidrológico ya calibrado en HEC-HMS para generar hidrogramas de respuestas correspondientes a los periodos de retorno de 10, 100 y 500 años. Para ello se utilizarán hietogramas sintéticos generados para los periodos de retorno mencionados con ayuda de los notebooks [***09_Hietogramas_sinteticos***]() y [***00_Funciones_hidro***]().
 > La guía y ficheros de este módulo se encuentran [**aquí**]()
# Como ejecutar los notebooks

Los notebooks pueden ser seguidos de dos formas: Localmente mediante instalando Python y Jupyter y en la nube sin necesidad de instalar nada en el computador mediante [Google Colab ](https://colab.research.google.com/). La primera forma requiere de la instalación previa de python, así como, de jupyter y de las librerías necesarias para la ejecución de los notebooks (En el repositorio se cuenta con un entorno que tiene las librerias necesarias, sin embargo, podrían preentarse problemas de compatibilidad). Por otra parte, para usar google Colab se requiere de una cuenta de [Google](https://www.google.com/intl/es/account/about/)

|Abre Colab para ejecutar los notebooks pulsando aquí abajo|
|:-:|
|[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)|

# Licencia

La documentación en este repositorio se encuentra protegida bajo la licencia [GNU Free Documentation License Version 1.3](https://www.gnu.org/licenses/fdl-1.3.html)

    Copyright (C)  2023 Juan Pablo García Montealegre.
    Permission is granted to copy, distribute and/or modify this document
    under the terms of the GNU Free Documentation License, Version 1.3
    or any later version published by the Free Software Foundation;
    with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts.
    A copy of the license is included in the section entitled "GNU
    Free Documentation License"
    
Los notebooks contenidos en este repositorio se encuentran protegidos bajo la licencia [GNU General Public License Version 3](https://www.gnu.org/licenses/gpl-3.0.html#license-text).

    Copyright (C) <2023>  <Juan Pablo García Montealegre>

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>.


