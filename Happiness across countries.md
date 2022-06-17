```python
import pandas as pd
import plotly.express as px
import seaborn as sns
from matplotlib import pyplot as plt
import numpy as np
```


```python
Population = pd.read_csv('./1-Week-DS-Summer-2022/Section 1/archive/Crude suicide rates.csv')
Fac = pd.read_csv('./1-Week-DS-Summer-2022/Section 1/archive/Facilities.csv')
humRec = pd.read_csv('./1-Week-DS-Summer-2022/Section 1/archive/Human Resources.csv')
suicideRate = pd.read_csv('./1-Week-DS-Summer-2022/Section 1/archive/Age-standardized suicide rates.csv')
suicideRate = suicideRate.rename(columns={"2016" : "suicidal_Rate"})
yr2016 = pd.read_csv('./1-Week-DS-Summer-2022/Section 1/archive2/2016_report.csv')
yr2020 = pd.read_csv('./1-Week-DS-Summer-2022/Section 1/archive2/2020_report.csv')
yr2019 = pd.read_csv('./1-Week-DS-Summer-2022/Section 1/archive2/2019_report.csv')
yr2018 = pd.read_csv('./1-Week-DS-Summer-2022/Section 1/archive2/2018_report.csv')
yr2017 = pd.read_csv('./1-Week-DS-Summer-2022/Section 1/archive2/2017_report.csv')
yr2015 = pd.read_csv('./1-Week-DS-Summer-2022/Section 1/archive2/2015_report.csv')
yr2016 = yr2016.rename(columns={"country" : "Country"})
merge_data = pd.merge(suicideRate, yr2016, on=['Country'])
df = pd.DataFrame(merge_data)
Both_sexes = df.loc[df["Sex"] == " Both sexes"]
```


```python
yr2020 = pd.read_csv('./1-Week-DS-Summer-2022/Section 2/1personProjHenry/2020_report.csv')
Population = pd.read_csv('./1-Week-DS-Summer-2022/Section 2/1personProjHenry/Crude suicide rates.csv')
yr2020.rename(columns={"country" : "Country"}, inplace=True)
mergedDfcool = pd.merge(Population, yr2020, on=['Country'])
# mergedDfcool.columns = merged_df.columns.str.replace('to', '-')
```

## Introduction to the data



#### Opening Statement

Suicide is self\-inflicted death with the desire to die. It is a major health concern, and is growing into one of the leading causes of death in many countries. 

Many variables can either increase or decrease the chance of suicide. We would assume a person’s happiness score plays an important role towards whether a person has suicidal ideation, which is the thought or planning of suicide.




```python
fig2 = px.scatter(Both_sexes, x="suicidal_Rate", y="happiness_score", color="continent", title="Happiness",
                 size='gdp_per_capita', hover_data=['Country'])
fig2.update_layout(
    yaxis_title="Happiness",
    )
fig2.update_layout(
    xaxis_title="Suicide Rate",
    )

fig2.show()
```




![png](Happiness%20across%20countries_files/S1HbyCountry.png)



According to this scatter plot, when putting the happiness scores and suicide rates together, they do not have a strong correlation with eachother. If suicidal ideation were to be correlated with happiness, there would be a much higher suicide rate when there is low happiness score. 




```python
fig = px.bar(Both_sexes.head(20), x="Country", y="happiness_score", title="Happiness")
fig.update_layout(
    yaxis_title="Happiness",
    )

fig.show()
```




![png](Happiness%20across%20countries_files/S1HvSscatterplot.png)



In this graph, it shows the average happiness score in selected countries for both sexes. It helps to visualize a wide range of happiness throughout the countries and how they differ with each other.




```python
fig = px.bar(merge_data.head(60), x="Country", y="suicidal_Rate", color="Sex", barmode='group', title="Suicide Rate")

fig.update_layout(
    yaxis_title="Suicide Rate",
    )
fig.show()
```




![png](Happiness%20across%20countries_files/S1SSRbyCountry.png)


This graph shows the suicide rate in those same countries but for males, females, and the average for both those sexes. It helps with seeing how vastly different the suicide rate is for the two sexes in that specific country and how it compares with other countries.



People speculate that suicide, or suicidal ideation, depends on how high a person's happiness score is. But, we were proven wrong with the data shown above. It was found that suicidal ideation doesn’t necessarily correlate with happiness.



## Government and Happiness




```python
fig = px.bar(Both_sexes.head(20), x="Country", y="happiness_score", title="Happiness")
fig.update_layout(
yaxis_title="Happiness",
)
fig.show()

```




![png](Happiness%20across%20countries_files/S1HbyCountry.png)



**Happiness Score for each country**

This bar graph shows the happiness score in Afghanistan, Albania, Algeria, Argentina, Australia, Azerbaijan, Bahrain, Bangladesh, Belarus, Belgium, Benin, Bosnia and Herzegovina, Botswana, Brazil, Bulgaria, Burkina Faso, Burundi, and Cambodia.

This is important because it helps you understand what the over all happiness is like, showing you if its an average high or average low.



```python
#happiness scores and social support
happinessscore = ["Afghanistan(25.669)", "Albania(48.827)"]
socialsupport = [35.6434, 83.0484]
plt.figure(figsize=(16,12))
sns.barplot(x=happinessscore, y=socialsupport)
plt.xlabel("Happiness Score Percentages")
plt.ylabel("Social Support Percentages")
plt.title("Happiness Scores and Social Support")
plt.show()

```




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_15_0.png)
    



**Happiness Scores and Social Support** 

This is a bar graph that shows the social support percentage correlated to happiness score in Afghanistan and Albania.

This is important because it shows you how in different countries with different social supports affect the happiness score of countries in a major way going back to the previous graph Afghanistan has a lower percentage then Albania. Further more it shows how gavernment effects the happiness of certain countries 



```python
#happiness scores in northern europe
happinessscore = [78.087, 76.456, 75.599, 75.045, 74.880]
country = ["Finland", "Denmark","Switzerland","Iceland","Norway"]
plt.figure(figsize=(16,12))
sns.barplot(x=country, y=happinessscore)
plt.xlabel("Countries")
plt.ylabel("Happiness Score Percentages")
plt.title("Happiness Scores in Northern European Countries")
plt.show()
```




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_17_0.png)
    



**Happiness Scores in Northern European Countries** 

This is a bar graph show the happiness score percentage of northern European countries 

This is important because it helps visualize what the northern European countries are experiencing when it comes down to the happiness level of those countries 




```python
#happiness scores vs government trust
happinessscore = ["Albania(48.827)", "Finland(78.087)"]
governmenttrust = [2.5361, 47.7857]
plt.figure(figsize=(16,12))
sns.barplot(x=happinessscore, y=governmenttrust)
plt.xlabel("Happiness Scores as Percentages")
plt.ylabel("Government Trust Percentage")
plt.title("Happiness Scores and Government Trust")
plt.show()
#blue is Albania and Orange is Finland
```




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_19_0.png)
    



###### Happiness Scores and Government Trust

This chart displays the happiness scores and government trust percentages of Albania and Finland. Albania has an extremely low percentage of government trust and a fairly low happiness score. In contrast, Finland has a very high percentage of both government trust and happiness. From this chart, it can be seen that countries who trust their government will be happier.




```python
#happiness scores vs freedom (shows that the more freedom people have, the happier they are)
happinessscore = ["Albania(48.827)", "Finland(78.087)"]
freedom = [46.1946, 66.2317]
plt.figure(figsize=(16,12))
sns.barplot(x=freedom, y=happinessscore)
plt.xlabel("Freedom Percentage")
plt.ylabel("Happiness Score Percentages")
plt.title("Happiness Scores VS Freedom")
plt.show()
#blue is Albania and Orange is Finland
```




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_21_0.png)
    



###### Happiness Scores and Freedom

This chart compares the freedom percentage in correlation with happiness scores between Finland and Albania. Albania has a fairly low percentage of freedom and happiness score. Finland has both a higher freedom percentage and happiness score.  

This shows that the more freedom citizens of 
a country are given, the happier they will be.




```python
plt.figure(figsize=(20,10))
g=sns.lineplot(data=merge_data,x="freedom",y="happiness_score", sort=True)

plt.xlabel("Freedom")
plt.ylabel("Happiness")
plt.show()
```




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_23_0.png)
    



##### Happiness Scores and Freedom

This chart shows the correlation between happiness scores and freedom throughout several countries. As freedom increases on the chart, so does the happiness score of the countries.

This further reinforces the idea that the more freedom countries are given, the happier they will be.



**Summary** 

As you saw this section went over how Albania is happier than Afghanistan due to the certain environmental factors shown in the graphs as well as the overall happiness of Northern European Countries. and one of these factors was social support leading on to the next section 


## How your social situation affects your happiness




```python
fig = px.bar(Both_sexes.head(20), x="Country", y="happiness_score", title="Happiness")
fig.update_layout(
    yaxis_title="Happiness",
    )

fig.show()
```


![png](Happiness%20across%20countries_files/S3HbyCountry.png)


This chart represents the happiness levels per country overall for both sexes. The happiness level does vary from country to country, and they are all very different because of the factors around these countries the differences. This is important since each of these countries are all very different, you can see where these countries stand in their level of happiness. 




```python
plt.figure(figsize=(20,10))
g=sns.lineplot(data=merge_data,x="family",y="happiness_score", sort=True)

plt.xlabel("Family")
plt.ylabel("Happiness")
plt.show()
```




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_29_0.png)
    



This chart shows the affect of family and how it boosts the level of happiness. This factor positively affects the level of happiness as the more family increases, the level of happiness does overall as well. Based on this data, if you are feeling unhappy, you should go 
see your family as they increase the levels of happiness.




```python
plt.figure(figsize=(20,10))
g=sns.lineplot(data=merge_data,x="health",y="happiness_score", sort=True)

plt.xlabel("Health")
plt.ylabel("Happiness")
plt.show()
```




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_31_0.png)
    



This chart shows the correlation between how healthy an individual is and how happy they are. It shows that being healthy generally leads to someone being more happy. Health is not the strongest factor in a person 's happiness, but it is one of the only factors that a person has control over. This is why it is important for you to lead a healthy life style.




```python
#happiness scores and social support
happinessscore = ["Afghanistan(25.669)", "Albania(48.827)"]
socialsupport = [35.6434, 83.0484]
plt.figure(figsize=(16,12))
sns.barplot(x=happinessscore, y=socialsupport)
plt.xlabel("Happiness Score Percentages")
plt.ylabel("Social Support Percentages")
plt.title("Happiness Scores and Social Support")
plt.show()
#blue is Afghanistan, orange is Albania
```




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_33_0.png)
    



This graph shows the happiness score for Afghanistan and Albania and the social support percentage. This shows that the more social support people in a country receive the happier that person tends to be. This is why it is important to 
surround yourself with family and friends that will support you.



**Over All Summary** 

Based on the following charts listed above, all of these factors can both negatively and positively affect peoples happiness, and how they feel overall. 

So in short the over all happiness in the world is affected by the environment around a person. Going back to our graphs you can see that the happiness is effected by Social Support, Family, Government Trust which are all factors people have little control over. There are some factors that someone does have control over, such as their health. Health is a major factor that a person can control and also has a huge affect on a persons happiness as shown by the graphs above. So once again, peoples overall happiness is affected by many environmental factors that they have little control over. That is why it is important to do the things 
we can control. I would encourage everyone to go visit your family, get the support that you need, and live a healthy life style. 


