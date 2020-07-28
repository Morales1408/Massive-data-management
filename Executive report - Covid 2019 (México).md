# Mexico in COVID-19 times

#### Brenda Martín Varguez, Fatima Martínez Torres, Mario Morales Zapata
#### July 27, 2020




## Table of contents
1. [Introduction](#introduction)
2. [Understanding the data](#understanding)


## Introduction <a name="introduction"></a>
The current situation the world is facing got us by surprise, this can be noticed just by looking at the news and paying attention to the thousands of death this tragic event 
has been causing; nonetheless, the impact of COVID-19 varies in function to the geographical position in which it takes place. 

Unfortunately, everything points to the fact that this Asian virus is here to stay, and remedies such as a vaccine or a very efficient treatment do not seem like a realistic solution in a short time period.
Meanwhile, Mexican society and the government had joined their resources in order to make the impact in public health more bearable for a greater good, but following the previous idea, the most logical questions raise... Does the data say Mexico is handling the situation properly? do we have any weak points we can improve? what else can we do?

The aim of this project is to take a step forward in order to solve those questions by looking into the real data so we can have an accurate perception of our national situation. In order for us to do so, we had done an Exploratory Data Analysis on the information provided by the Mexican goverment through their public database on COVID-19, which you can watch [in here](https://datos.gob.mx/busca/dataset/informacion-referente-a-casos-covid-19-en-mexico).

It is worth to say that the analysis done for this project's purpose was done in the information retrieved from July 16 to July 27 of this year.

## Understanding the data <a name="understanding"></a>
As we have written before, the analysis was done in the data retrieved from July 16 to July 27 of this year, during these days we recollected the information of __4,891,039 people__, but what do we know about them and what can we obtain from it? This is what [Datos Abiertos](https://datos.gob.mx/busca/dataset/informacion-referente-a-casos-covid-19-en-mexico) gave us acces to:


|Variable name|Type|Description|
|:------|:-----|:------|
|fecha_actualizacion|str|It tells the last date when that entrie was updated|
|id_registro|str|It tells the specific person's Id|
|origen|int|It tells whether the person came from the USMER or not|
|sector|int|It tells the person's medical institute procedence|
|entidad_um|int|__CORREGIR___|
|sexo|int|It tells the person's sex|
|entidad_nac|int| __CORREGIR__|
|entidad_res|int|It tells the person's residence entity|
|municipio_res|int|It tells the person's municipality of residence|
|tipo_paciente|int|It tells whether the person is ambulatory, hospitalized, or unknown|
|fecha_ingreso|str|It tells the person's entry date|
|fecha_sintomas|str|It tells the date of the person's first symptoms|
|fecha_def|str|It tells the person's date of death|
|intubado|int|It tells the person's status related to being intubated|
|neumonia|int|
