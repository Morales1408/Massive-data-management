# Mexico in COVID-19 times

#### Brenda Martín Varguez, Fatima Martínez Torres, Mario Morales Zapata
#### July 27, 2020




## Table of contents
1. [Pipeline](#pipeline)
2. [Introduction](#introduction)
3. [Understanding the data](#understanding)
4. [Exploratory Data Analysis](#eda)
5. [Algorithm implemented](#algorithm implemented)
6. [Conclusion](#conclusion)

## Pipeline <a name="pipeline"></a>
As a closure for the Big Data Management course, we are to develop a project involving topics that the management of data requires, where we, as a team, could get something valuable.

Thus, for the development of a pipeline, we are to follow some specific requirements:
* **Problem:** To choose a current problematica on the IT industry, or not related at all.
* **Solutions:** Those that have been already applied to solve the problem.
* **Data source:** Either internal and external.
* **Posible algorithms**
* **Data cleaning and manipulations:** Icluiding...
    * Variables
    * Data
    * Algorithm
    * Target Variables
    * Calculations and Formulas
    * Decision making
    * Concrete actions
    * Dasboards

The project must consider:
* **Scalability** justifying the election of the tools and technologies used for the proyect.
* **Replicability** offering the posibillity to provide the same analysis specifying the own requirements of data.

The team decided to choose a current topic that the entire world faces and deals with, including the health sector, the industrial sector, even the agricultural sector or even the academic sector. COVID-19 has shown its presence on anyone's lifes.

Our approach will be focused on our country: Mexico. With the purpose of finding interesting information for us wich might lead us to a deeper analysis.

The main justification of the election of such topic, is that the data can be found online due to different sectors that provide API's with the registered data related to this pandemia. Or at least that was we tought.

Our proposal is guided by our knowledge and a value added by making a prediction with Machine Learning.

The first thing to do was to search for the information needed. Surfing the web, we found many data sources, that collect the most common information: number of cases registered, number of deaths, and country. Even though the plenty of web pages that describe the topic and provide data related, the first thing we struggle with was to found a full database that gives valuable information. Many of them were out-to-date and barely accessible according to our limited resources. The latter was the case of the API of the Mexican Government.

The initial idea, therefore, of getting the data from a public repository was denied by the circumstances.

Nonetheless, our research continued and we found the data source we used for the project taken from [CDMX data](https://datos.gob.mx/busca/dataset/informacion-referente-a-casos-covid-19-en-mexico) which also stores national information, which fulfiled our needs.

Once we accessed to the data, we started with a script in Bash from Linux, to later connect it with Apache Airflow in order to update the information every 24 hours.
Whit this, though, the more we advanced with the script on Bash, the more difficult was Airflow due to some problems when using the operators needed and the way we should have used the parameters. That is why we decided to keep our csv files obtained directly from the script of Bash, instead pf using the Airflow technology. From here, it is important to mention that the information taken was from July 16 to July 27 of this year, the time we declared on the script to store the data, and with the main purpose of having enough data to use it on the prediction.

Now, we had our data acquisition ready, but we needed also to store it for us to use it for its analysis. Therefore, our initial idea was to create and store the database in a cluster from MongoDB, speciffically in MongoDB Atlas, because we needed a communitary service to thet three of us to easily access to the documents. We had ready the cluster. However, when trying to upload our file, we faced the problem of the limitation of storage on a shared cluster in MongoDB Atlas. Thus, we decided to keep it in the limited space, since there was still enough data to be able to work with. And mainly, because we had the original plan of using Tableau for the data visualization part of our project, and MongoDB offers this connection.

However, more difficulties began to be present while getting advances in the project. Since we wanted to switching from MongoDB Atlas to Tableau the platform required an upgrade in the cluster that would allow us to complete said connection. And the cost was of $0.08 per hour of usage. Therefore we look for an alternative and found that Tableau gives the opportunity to be connected with OneDrive, and since we store our files for protection in that platform provided by our University, we decided to work in such way.

Finally, the data analysis was complemented with Jupyter Notebook due to its practicality and our experience with this tool. Therefore, our pipeline for this project is as shown below:

![](/covidd/pipeline(2).jpg)

## Introduction <a name="introduction"></a>
The current situation the world is facing got us by surprise, this can be noticed just by looking at the news and paying attention to the thousands of death this tragic event 
has been causing; nonetheless, the impact of COVID-19 varies in function to the geographical position in which it takes place. 

Unfortunately, everything points to the fact that this virus is here to stay, and remedies such as a vaccine or a very efficient treatment do not seem like a realistic solution in a short time period.
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
|entidad_um|int|It tells the person's medical unity entity |
|sexo|int|It tells the person's sex|
|entidad_nac|int|It tells the person's birht entity|
|entidad_res|int|It tells the person's residence entity|
|municipio_res|int|It tells the person's municipality of residence|
|tipo_paciente|int|It tells whether the person is ambulatory, hospitalized, or unknown|
|fecha_ingreso|str|It tells the person's entry date|
|fecha_sintomas|str|It tells the date of the person's first symptoms|
|fecha_def|str|It tells the person's date of death|
|intubado|int|It tells the person's status related to being intubated|
|neumonia|int|It tells the peron's status relateed to having pneumonia|
|edad|int|It tells the person's age|
|nacionalidad|int|It tells whether the person is mexican, foreigner or unknown|
|embarazo|int|It tells the person's status on pregnancy|
|habla_lengua_indig|int|It tells whether the person speaks a indigenous language or not, or if is unknown|
|diabetes|int|It tell the person's status related to diabetes|
|epoc|int|It tells the person's status related to epoc|
|asma|int|It tells the person's status related to asthma|
|inmuspurt|int|It tells the person's status related to immunosuppression|
|hipertension|int|It tells the person's status related to hypertension|
|otra_com|int|It tells the person's status related to having another complication|
|cardiovascular|int|It tells the person's status related to having a cardiovascular issue|
|obesidada|int|It tells the person's status related to being obese|
|renal_cronica|int|It tells the person's status related to having a chronic kidney disease|
|tabaquismo|int|It tells the person's status related to smoking|
|resultado|int|It tells the person's status on his/her COVID test|
|migrante|int|It tells the person's status related to being migrant|
|pais_nacionalidad|str|It tells the person's nationality country|
|pais_origen|str|It tells the person's country of birth|

For further understanding, you can read the [official data dictionary](https://upy-my.sharepoint.com/:x:/g/personal/st1809116_upy_edu_mx/EcOTfYXfGUlLoRqsyoLhpjkBRurV2mrMzQUH9W4sTiqThg?e=QbUeJH) in here. 

## Exploratory data analysis <a name="eda"></a>

To begin with, we wanted to determine the amount of people that are indeed SARS-CoV-2 positive so we can have an idea on the impact of the virus in our four million patients. 

Here's the result. 

![](/covidd/pete.png)

As we can see, even though the amount of negative cases is bigger than the positive ones, it is quite a preoccupation that the amount of people with the virus cases is getting close to fifty percent of our entire registered population.



Another thing that was from our concern was to know the sectors that are more likely to provide the data from a positive case; here is the distribution we found.

![](/covidd/cambiar.png)

The result we found was shocking for us. Considering our analyzed population to be more than __2,000,000__ infected people, it is quite interesting to find that we could basically name two sectors as responsibles for testing all positive cases. It is true the IMSS is the biggest hospital institute in Mexico; nonetheless, the SSA shows to be more important in this case. Meanwhile, the impact in positive cases testing for the remaining institutes is almost negligible compared to both of them. 


Another thing of our interest was to find the proportion there is between infected women and men, is it fair to say that are man more likely to be positive? is it the other way around? 

Here is what we found

![](/covidd/pete2_2.png)

Even though we are talking about thousands of people of difference, the gap between sex is not big enough to be really the center of attention for a specific analysis. Unfortunately for us, everyone seems to be equally susceptible to get the virus. 


Continuing with the Analysis, we found that there are a lot of different nationalities in the database, so it might be important to know the top ten nationalities with more patients that are being treated in Mexico. This measurement could get us some insight into the impact of tourism in our country and how that could potentially increase the risk in other nations.

![](/covidd/pete3.png)


Once we saw that image, the decisions took by several governments of closing airports makes total sense. It is very dangerous for both countries to have infected people coming home or going somewhere else as tourists. 

As it was written in the beginning, the probability you have of being infected varies according to your geological position, this is why we decided to see the states where we can find a big concentration of the cases so we can have an objective idea of the most dangerous places in Mexico; in that way, we might consider to take a look into the distribution of material and resources. 

![](/covidd/cambiar2.png)

As expected, the most populated states are the ones with a higher concentration of the national cases; nevertheless, it is important to point out that both Mexico city and the State of Mexico (México) are relatively small compared to other states of the republic, so both cities should, according to the data, center of attention because of their territory and population. 

Now, with the previous graph, we can infer the places where the hospital's capacity might be to its limit; nonetheless, that does not necessarily mean that the hospital attention is bad for the patients. This got us intrigued and we wanted to find a type of measure within the dataset that might provide us with some answer. What we finally did was to take into consideration all that infected population that unfortunately died, then, we measure the time it took them to be in the hospital until their las day. 

This are our results
![](/covidd/pete10.png)

That could be a really interesting topic to dig about, why the patients that are going to die got to live three more days if they live in Queretaro than if they were being treated in Morelos? is it related to the doctors? to the patients? to the resources? Regardless of the answer is something that must be a concern for all of us.  

Now, focusing on the population, we wanted to find for factors or conditions that might be taken into consideration for the medical squad to target in a better or faster way that segment of the population that can potentially have the worst response to the virus by becoming patients.

First of all, we wanted to see for the patients' previous conditions while being diagnosed with COVID.

![](/covidd/pete12.png)

It is not a secret to tell that Mexico's population's health is not the best, but is something really worrying about the fact that not even half of the patients were free of, at least, one of those diseases. Is it because they are more vulnerable to get infected? Is it because of Mexico's population? Definitely is worth the shot to investigate. Now that we have seen that previous conditions are a common denominator in Mexican COVID patients, we wanted to determine the risk of having any of those health issues. 
What we did was to divide our population into those ones that have, at least, one of those ailments in population segments; then, we divided each population segment and calculate the percentage of people that died because of that ailment. With that, we calculated the probability you have to die in case you have any of those previous conditions. 



![](/covidd/pete11.png)


This is one of the most important insights we got from the dataset, it is extremely important to pay attention to previous conditions because there are cases like pneumonia or having a cronical kidney disease that increase your probability to die considerably, besides that, we have just seen that having these conditions are more common than we would like. 

Finally, we have seen in other parts of the world that age is something to take into consideration while detecting a potential chronic patient, hence, we measured the age distribution in our country.

![](/covidd/pete8.png)

As expected by being a natural variable, it proved to have a normal behaviour (this was mathematically proved with a Kolmogorov-Smirnov and a Shapiro-Wilks test; both of them with a p<0.05). We could easily say that our population has a huge range, but the mean lies on people that are considered to be middle aged.Now, does the age matter in Mexico to became a chronic patient? 

In order to answer the previous question (and once we knew our variable was normally behaved), we noticed that being intubated is something that only apply for those patients that are extremely bad; hence, we tested (with a two-tailed t-student test) the distribution of the age of the people that are not intubated against the distribution of those ones that are. The results were to tell us if the age is statistically a factor that forced people to be intubated. 

![](/covidd/pete9.png)

Our test yielded (with a p<0.05) that older people are indeed more susceptible to get intubated. This is, age is in fact an important factor to consider for patients.

## Algorithm implemented <a name="algorithm"></a>

Logistic Regression is a supervised learning algorithm used for classification problems. Classification can be defined as the task of predicting a discrete class label. In a classification problem, data is classified into one of two or more classes. A classification problem with two classes is called *binary*. More than two classes is called a *mul-ticlass* classification. Logistic regression it’s a regression method that allows estimating the probability of a categorical variable based on a numerical variable. One of the main applications of logistic regression is that of binary classification, in which observations are classified into one group or another depending on the value of the variable used as a predictor.

In this case, we are seeking to predict if a patient who has COVID-19 and medical conditions such as a diagnosis of EPOC, chronic renal insufficiency, pneumonia, obesity, hypertension, asthma, diabetes, immunosuppression or any other disease; will be intubated or not. In this way, hospitals can prepare themselves to have enough of the equipment necessary for all patients who will need to be intubated.  We are also taking into consideration the age and sex of each patient.

The table below shows the final data frame that will be used.

| Variable name  |   Type  |                                       Description                                       |       Source file       |
|----------------|:-------:|:---------------------------------------------------------------------------------------:|:-----------------------:|
|       sex      | boolean | Identifies the sex of the patient. 1: female, 0: men                                    | created                 |
|    intubado    | boolean | Identifies if the patient required intubation. 1: yes, 0: no                            | created                 |
|    neumonia    | boolean | Identifies if the patient was diagnosed with pneumonia. 1: yes, 0: no                   | created                 |
|      edad      | integer | Identifies the patient's age.                                                           | 200722COVID19MEXICO.csv |
|    embarazo    | boolean | Identifies if the patient is pregnant. 1: yes, 0: no                                    | created                 |
|    diabetes    | boolean | Identifies if the patient was diagnosed with diabetes. 1: yes, 0: no                    | created                 |
|      epoc      | boolean | Identifies if the patient has a diagnosis of EPOC. 1: yes, 0: no                        | created                 |
|      asma      | boolean | Identifies if the patient has a diagnosis of asthma. 1: yes, 0: no                      | created                 |
|    inmusupr    | boolean | Identifies if the patient has immunosuppression. 1: yes, 0: no                          | created                 |
|  hipertension  | boolean | Identifies if the patient has a diagnosis of hypertension. 1: yes, 0: no                | created                 |
|    otras_com   | boolean | Identifies if the patient is diagnosed with other diseases. 1: yes, 0: no               | created                 |
| cardiovascular | boolean | Identifies if the patient has a diagnosis of cardiovascular disease. 1: yes, 0: no      | created                 |
|    obesidad    | boolean | Identifies if the patient has been diagnosed with obesity. 1: yes, 0: no                | created                 |
|  renal_cronica | boolean | Identifies if the patient has been diagnosed with chronic kidney failure. 1: yes, 0: no | created                 |
|   tabaquismo   | boolean | Identifies if the patient has a smoking habit. 1: yes, 0: no                            | created                 |



## Conclusion <a name="conclusion"></a>

Unfortunately, there is still a lot to be said about the COVID-19 in Mexico and in the world, so the best we can do is to learn as much as we can about it to take care of our people. 

That is what we tried to do with our project, we found some good insights about the characteristics of our populations such their previous healt condition and their age (which we learned is an important characteristic to consider), but most importantly, we raised some questions that we consider to be worth of a research, such the hospital conditions of the states where the people live longer. 

We hope this project fulfilled its mission and contribuited a little bit to this topic to make it more bearable during this though times.
