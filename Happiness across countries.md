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




<html>
<head><meta charset="utf-8" /></head>
<body>
    <div>            <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-AMS-MML_SVG"></script><script type="text/javascript">if (window.MathJax) {MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}</script>                <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script src="https://cdn.plot.ly/plotly-2.4.2.min.js"></script>                <div id="03035141-c2bf-40c2-8807-9b7835bb50cf" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("03035141-c2bf-40c2-8807-9b7835bb50cf")) {                    Plotly.newPlot(                        "03035141-c2bf-40c2-8807-9b7835bb50cf",                        [{"customdata":[["Afghanistan"],["Armenia"],["Azerbaijan"],["Bahrain"],["Bangladesh"],["Cambodia"],["China"],["Cyprus"],["Georgia"],["India"],["Indonesia"],["Iraq"],["Israel"],["Japan"],["Jordan"],["Kazakhstan"],["Kuwait"],["Kyrgyzstan"],["Lebanon"],["Malaysia"],["Mongolia"],["Myanmar"],["Nepal"],["Pakistan"],["Philippines"],["Saudi Arabia"],["Singapore"],["Sri Lanka"],["Tajikistan"],["Thailand"],["Turkey"],["Turkmenistan"],["United Arab Emirates"],["Uzbekistan"],["Yemen"]],"hovertemplate":"continent=Asia<br>suicidal_Rate=%{x}<br>happiness_score=%{y}<br>gdp_per_capita=%{marker.size}<br>Country=%{customdata[0]}<extra></extra>","legendgroup":"Asia","marker":{"color":"#636efa","size":[0.31982,0.7682100000000001,1.02389,1.32376,0.39753,0.46038,0.89012,1.20813,0.7419,0.64499,0.8282700000000001,0.98549,1.2285700000000002,1.27074,0.90198,1.12254,1.5542200000000002,0.47428,1.02564,1.12486,0.82819,0.27108,0.3599699999999999,0.59543,0.70532,1.39541,1.52186,0.83524,0.39047,0.9669,1.06098,0.95847,1.42727,0.63244,0.5464899999999999],"sizemode":"area","sizeref":0.003909775,"symbol":"circle"},"mode":"markers","name":"Asia","orientation":"v","showlegend":true,"type":"scatter","x":[6.4,5.7,2.6,5.7,6.1,5.9,8.0,4.5,6.7,16.5,3.7,4.1,5.2,14.3,3.7,22.8,2.2,9.1,3.2,6.2,13.3,8.1,9.6,3.1,3.7,3.4,7.9,14.2,3.3,12.9,7.2,7.2,2.7,7.4,9.8],"xaxis":"x","y":[3.575,4.35,5.2120000000000015,5.96,4.694,3.819,5.14,5.689,4.297,4.565,5.399,4.677,7.278,5.987,5.192,5.855,6.295,5.2860000000000005,4.839,5.77,4.874,4.307,4.513999999999999,5.194,5.073,6.4110000000000005,6.797999999999999,4.271,4.7860000000000005,6.455,5.332000000000002,5.547999999999999,6.901,6.002999999999999,4.077],"yaxis":"y"},{"customdata":[["Albania"],["Austria"],["Belarus"],["Belgium"],["Bosnia and Herzegovina"],["Bulgaria"],["Croatia"],["Denmark"],["Estonia"],["Finland"],["France"],["Germany"],["Greece"],["Hungary"],["Iceland"],["Ireland"],["Italy"],["Latvia"],["Lithuania"],["Luxembourg"],["Malta"],["Montenegro"],["Netherlands"],["Norway"],["Poland"],["Portugal"],["Romania"],["Serbia"],["Slovakia"],["Slovenia"],["Spain"],["Sweden"],["Switzerland"],["Ukraine"]],"hovertemplate":"continent=Europe<br>suicidal_Rate=%{x}<br>happiness_score=%{y}<br>gdp_per_capita=%{marker.size}<br>Country=%{customdata[0]}<extra></extra>","legendgroup":"Europe","marker":{"color":"#EF553B","size":[0.8786700000000001,1.33723,1.0319200000000002,1.30782,0.8322299999999999,1.01216,1.08254,1.32548,1.15174,1.29025,1.27778,1.32792,1.15406,1.12094,1.30232,1.33596,1.25114,1.11312,1.14723,1.56391,1.2074,0.97438,1.32944,1.459,1.12555,1.15991,1.04345,0.92053,1.16891,1.18498,1.23011,1.33171,1.39651,0.79907],"sizemode":"area","sizeref":0.003909775,"symbol":"circle"},"mode":"markers","name":"Europe","orientation":"v","showlegend":true,"type":"scatter","x":[5.6,11.4,21.4,15.7,6.4,7.9,11.5,9.2,14.4,13.8,12.1,9.1,3.8,13.6,13.3,10.9,5.5,17.2,25.7,10.4,6.5,7.9,9.6,10.1,13.4,8.6,8.0,10.9,10.1,13.3,6.1,11.7,11.3,18.5],"xaxis":"x","y":[4.959,7.2,5.813,6.937,4.949,4.218,5.759,7.527,5.428999999999999,7.4060000000000015,6.575,6.75,4.857,4.8,7.561,6.94,5.948,5.098,5.8329999999999975,6.9460000000000015,6.3020000000000005,5.192,7.377999999999999,7.522,5.791,5.102,5.124,5.122999999999998,5.995,5.848,6.329,7.364,7.5870000000000015,4.681],"yaxis":"y"},{"customdata":[["Algeria"],["Benin"],["Botswana"],["Burkina Faso"],["Burundi"],["Cameroon"],["Chad"],["Egypt"],["Ethiopia"],["Gabon"],["Ghana"],["Kenya"],["Liberia"],["Libya"],["Madagascar"],["Malawi"],["Mali"],["Mauritania"],["Mauritius"],["Morocco"],["Niger"],["Nigeria"],["Rwanda"],["Senegal"],["Sierra Leone"],["South Africa"],["Togo"],["Tunisia"],["Uganda"],["Zambia"],["Zimbabwe"]],"hovertemplate":"continent=Africa<br>suicidal_Rate=%{x}<br>happiness_score=%{y}<br>gdp_per_capita=%{marker.size}<br>Country=%{customdata[0]}<extra></extra>","legendgroup":"Africa","marker":{"color":"#00cc96","size":[0.93929,0.28665,0.99355,0.2581199999999999,0.0153,0.4225,0.34193,0.8818,0.1907299999999999,1.06024,0.5455800000000001,0.36471,0.0712,1.13145,0.20824,0.01604,0.26074,0.45407,1.00761,0.7347899999999999,0.0694,0.65435,0.22208,0.36498,0.33024,0.92049,0.20868,0.88113,0.2110199999999999,0.47038,0.271],"sizemode":"area","sizeref":0.003909775,"symbol":"circle"},"mode":"markers","name":"Africa","orientation":"v","showlegend":true,"type":"scatter","x":[3.3,15.7,11.5,14.8,15.0,19.5,15.5,4.4,11.4,9.6,8.7,5.6,13.4,5.5,6.9,7.8,8.9,7.5,7.3,3.1,9.0,17.3,11.0,11.8,16.1,12.8,16.6,3.2,20.0,11.3,19.1],"xaxis":"x","y":[5.605,3.34,4.332,3.587,2.905,4.252,3.667,4.194,4.512,3.896,4.633,4.419,4.5710000000000015,5.754,3.681,4.292,3.995,4.436,5.477,5.013,3.845,5.268,3.465,3.904,4.507,4.642,2.839,4.739,3.931,5.129,4.61],"yaxis":"y"},{"customdata":[["Argentina"],["Brazil"],["Chile"],["Colombia"],["Costa Rica"],["Dominican Republic"],["Ecuador"],["El Salvador"],["Guatemala"],["Guinea"],["Haiti"],["Honduras"],["Jamaica"],["Nicaragua"],["Panama"],["Paraguay"],["Peru"],["Uruguay"]],"hovertemplate":"continent=South America<br>suicidal_Rate=%{x}<br>happiness_score=%{y}<br>gdp_per_capita=%{marker.size}<br>Country=%{customdata[0]}<extra></extra>","legendgroup":"South America","marker":{"color":"#ab63fa","size":[1.05351,0.98124,1.10715,0.91861,0.95578,0.8953700000000001,0.8640200000000001,0.76454,0.74553,0.17417,0.26673,0.59532,0.81038,0.59325,1.06353,0.75985,0.9001899999999999,1.06166],"sizemode":"area","sizeref":0.003909775,"symbol":"circle"},"mode":"markers","name":"South America","orientation":"v","showlegend":true,"type":"scatter","x":[9.1,6.1,9.7,7.0,7.5,10.5,7.2,13.5,2.9,10.5,12.2,3.4,2.0,11.9,4.4,9.3,5.1,16.5],"xaxis":"x","y":[6.574,6.983,6.67,6.477,7.226,4.885,5.975,6.13,6.1229999999999976,3.656,4.518,4.788,5.709,5.827999999999999,6.7860000000000005,5.877999999999999,5.824,6.485],"yaxis":"y"},{"customdata":[["Australia"],["New Zealand"]],"hovertemplate":"continent=Australia<br>suicidal_Rate=%{x}<br>happiness_score=%{y}<br>gdp_per_capita=%{marker.size}<br>Country=%{customdata[0]}<extra></extra>","legendgroup":"Australia","marker":{"color":"#FFA15A","size":[1.33358,1.2501799999999998],"sizemode":"area","sizeref":0.003909775,"symbol":"circle"},"mode":"markers","name":"Australia","orientation":"v","showlegend":true,"type":"scatter","x":[11.7,11.6],"xaxis":"x","y":[7.284,7.286],"yaxis":"y"},{"customdata":[["Canada"],["Mexico"]],"hovertemplate":"continent=North America<br>suicidal_Rate=%{x}<br>happiness_score=%{y}<br>gdp_per_capita=%{marker.size}<br>Country=%{customdata[0]}<extra></extra>","legendgroup":"North America","marker":{"color":"#19d3f3","size":[1.32629,1.02054],"sizemode":"area","sizeref":0.003909775,"symbol":"circle"},"mode":"markers","name":"North America","orientation":"v","showlegend":true,"type":"scatter","x":[10.4,5.2],"xaxis":"x","y":[7.427,7.187],"yaxis":"y"}],                        {"legend":{"itemsizing":"constant","title":{"text":"continent"},"tracegroupgap":0},"template":{"data":{"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"geo":{"bgcolor":"white","lakecolor":"white","landcolor":"#E5ECF6","showlakes":true,"showland":true,"subunitcolor":"white"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"light"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"bgcolor":"#E5ECF6","radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"ternary":{"aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"bgcolor":"#E5ECF6","caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"title":{"x":0.05},"xaxis":{"automargin":true,"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","zerolinewidth":2}}},"title":{"text":"Happiness"},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"Suicide Rate"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Happiness"}}},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('03035141-c2bf-40c2-8807-9b7835bb50cf');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                            </script>        </div>
</body>
</html>






```python
fig = px.bar(Both_sexes.head(20), x="Country", y="happiness_score", title="Happiness")
fig.update_layout(
    yaxis_title="Happiness",
    )

fig.show()
```




<html>
<head><meta charset="utf-8" /></head>
<body>
    <div>            <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-AMS-MML_SVG"></script><script type="text/javascript">if (window.MathJax) {MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}</script>                <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script src="https://cdn.plot.ly/plotly-2.4.2.min.js"></script>                <div id="e73b242c-c094-41e1-a163-609f54f12c43" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("e73b242c-c094-41e1-a163-609f54f12c43")) {                    Plotly.newPlot(                        "e73b242c-c094-41e1-a163-609f54f12c43",                        [{"alignmentgroup":"True","hovertemplate":"Country=%{x}<br>happiness_score=%{y}<extra></extra>","legendgroup":"","marker":{"color":"#636efa","pattern":{"shape":""}},"name":"","offsetgroup":"","orientation":"v","showlegend":false,"textposition":"auto","type":"bar","x":["Afghanistan","Albania","Algeria","Argentina","Armenia","Australia","Austria","Azerbaijan","Bahrain","Bangladesh","Belarus","Belgium","Benin","Bosnia and Herzegovina","Botswana","Brazil","Bulgaria","Burkina Faso","Burundi","Cambodia"],"xaxis":"x","y":[3.575,4.959,5.605,6.574,4.35,7.284,7.2,5.2120000000000015,5.96,4.694,5.813,6.937,3.34,4.949,4.332,6.983,4.218,3.587,2.905,3.819],"yaxis":"y"}],                        {"barmode":"relative","legend":{"tracegroupgap":0},"template":{"data":{"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"geo":{"bgcolor":"white","lakecolor":"white","landcolor":"#E5ECF6","showlakes":true,"showland":true,"subunitcolor":"white"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"light"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"bgcolor":"#E5ECF6","radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"ternary":{"aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"bgcolor":"#E5ECF6","caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"title":{"x":0.05},"xaxis":{"automargin":true,"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","zerolinewidth":2}}},"title":{"text":"Happiness"},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"Country"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Happiness"}}},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('e73b242c-c094-41e1-a163-609f54f12c43');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                            </script>        </div>
</body>
</html>




```python
fig = px.bar(merge_data.head(60), x="Country", y="suicidal_Rate", color="Sex", barmode='group', title="Suicide Rate")

fig.update_layout(
    yaxis_title="Suicide Rate",
    )
fig.show()
```




<html>
<head><meta charset="utf-8" /></head>
<body>
    <div>            <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-AMS-MML_SVG"></script><script type="text/javascript">if (window.MathJax) {MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}</script>                <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script src="https://cdn.plot.ly/plotly-2.4.2.min.js"></script>                <div id="d6d438a1-8524-41e1-a3cf-1cc8453a7bff" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("d6d438a1-8524-41e1-a3cf-1cc8453a7bff")) {                    Plotly.newPlot(                        "d6d438a1-8524-41e1-a3cf-1cc8453a7bff",                        [{"alignmentgroup":"True","hovertemplate":"Sex= Both sexes<br>Country=%{x}<br>suicidal_Rate=%{y}<extra></extra>","legendgroup":" Both sexes","marker":{"color":"#636efa","pattern":{"shape":""}},"name":" Both sexes","offsetgroup":" Both sexes","orientation":"v","showlegend":true,"textposition":"auto","type":"bar","x":["Afghanistan","Albania","Algeria","Argentina","Armenia","Australia","Austria","Azerbaijan","Bahrain","Bangladesh","Belarus","Belgium","Benin","Bosnia and Herzegovina","Botswana","Brazil","Bulgaria","Burkina Faso","Burundi","Cambodia"],"xaxis":"x","y":[6.4,5.6,3.3,9.1,5.7,11.7,11.4,2.6,5.7,6.1,21.4,15.7,15.7,6.4,11.5,6.1,7.9,14.8,15.0,5.9],"yaxis":"y"},{"alignmentgroup":"True","hovertemplate":"Sex= Male<br>Country=%{x}<br>suicidal_Rate=%{y}<extra></extra>","legendgroup":" Male","marker":{"color":"#EF553B","pattern":{"shape":""}},"name":" Male","offsetgroup":" Male","orientation":"v","showlegend":true,"textposition":"auto","type":"bar","x":["Afghanistan","Albania","Algeria","Argentina","Armenia","Australia","Austria","Azerbaijan","Bahrain","Bangladesh","Belarus","Belgium","Benin","Bosnia and Herzegovina","Botswana","Brazil","Bulgaria","Burkina Faso","Burundi","Cambodia"],"xaxis":"x","y":[10.6,7.0,4.9,15.0,10.1,17.4,17.5,4.3,7.9,5.5,39.3,22.2,22.6,10.6,18.3,9.7,13.1,22.4,23.1,9.0],"yaxis":"y"},{"alignmentgroup":"True","hovertemplate":"Sex= Female<br>Country=%{x}<br>suicidal_Rate=%{y}<extra></extra>","legendgroup":" Female","marker":{"color":"#00cc96","pattern":{"shape":""}},"name":" Female","offsetgroup":" Female","orientation":"v","showlegend":true,"textposition":"auto","type":"bar","x":["Afghanistan","Albania","Algeria","Argentina","Armenia","Australia","Austria","Azerbaijan","Bahrain","Bangladesh","Belarus","Belgium","Benin","Bosnia and Herzegovina","Botswana","Brazil","Bulgaria","Burkina Faso","Burundi","Cambodia"],"xaxis":"x","y":[2.1,4.3,1.8,3.5,2.0,6.0,5.7,1.0,2.1,6.7,6.2,9.4,9.6,2.5,5.7,2.8,3.2,9.1,7.7,3.2],"yaxis":"y"}],                        {"barmode":"group","legend":{"title":{"text":"Sex"},"tracegroupgap":0},"template":{"data":{"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"geo":{"bgcolor":"white","lakecolor":"white","landcolor":"#E5ECF6","showlakes":true,"showland":true,"subunitcolor":"white"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"light"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"bgcolor":"#E5ECF6","radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"ternary":{"aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"bgcolor":"#E5ECF6","caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"title":{"x":0.05},"xaxis":{"automargin":true,"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","zerolinewidth":2}}},"title":{"text":"Suicide Rate"},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"Country"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Suicide Rate"}}},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('d6d438a1-8524-41e1-a3cf-1cc8453a7bff');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                            </script>        </div>
</body>
</html>



## Government and Happiness


```python
fig = px.bar(Both_sexes.head(20), x="Country", y="happiness_score", title="Happiness")
fig.update_layout(
yaxis_title="Happiness",
)
fig.show()

```




<html>
<head><meta charset="utf-8" /></head>
<body>
    <div>            <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-AMS-MML_SVG"></script><script type="text/javascript">if (window.MathJax) {MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}</script>                <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script src="https://cdn.plot.ly/plotly-2.4.2.min.js"></script>                <div id="2a834ac9-9cc7-47a3-a7d7-991f9ee54d8f" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("2a834ac9-9cc7-47a3-a7d7-991f9ee54d8f")) {                    Plotly.newPlot(                        "2a834ac9-9cc7-47a3-a7d7-991f9ee54d8f",                        [{"alignmentgroup":"True","hovertemplate":"Country=%{x}<br>happiness_score=%{y}<extra></extra>","legendgroup":"","marker":{"color":"#636efa","pattern":{"shape":""}},"name":"","offsetgroup":"","orientation":"v","showlegend":false,"textposition":"auto","type":"bar","x":["Afghanistan","Albania","Algeria","Argentina","Armenia","Australia","Austria","Azerbaijan","Bahrain","Bangladesh","Belarus","Belgium","Benin","Bosnia and Herzegovina","Botswana","Brazil","Bulgaria","Burkina Faso","Burundi","Cambodia"],"xaxis":"x","y":[3.575,4.959,5.605,6.574,4.35,7.284,7.2,5.2120000000000015,5.96,4.694,5.813,6.937,3.34,4.949,4.332,6.983,4.218,3.587,2.905,3.819],"yaxis":"y"}],                        {"barmode":"relative","legend":{"tracegroupgap":0},"template":{"data":{"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"geo":{"bgcolor":"white","lakecolor":"white","landcolor":"#E5ECF6","showlakes":true,"showland":true,"subunitcolor":"white"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"light"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"bgcolor":"#E5ECF6","radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"ternary":{"aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"bgcolor":"#E5ECF6","caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"title":{"x":0.05},"xaxis":{"automargin":true,"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","zerolinewidth":2}}},"title":{"text":"Happiness"},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"Country"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Happiness"}}},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('2a834ac9-9cc7-47a3-a7d7-991f9ee54d8f');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                            </script>        </div>
</body>
</html>



**Happiness Score for each country**

This bar graph shows the happiness score in Afghanistan, Albania, Algeria, Argentina, Australia, Azerbaijan, Bahrain, Bangladesh, Belarus, Belgium, Benin, Bosnia and Herzegovina, Botswana, Brazil, Bulgaria, Burkina Faso, Burundi, and Cambodia. 

This is important because it helps you understand what the over all happiness is like showing you if its an average high or average low. 



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




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_12_0.png)
    



**Happiness Scores and Social Support** 

This is a bar graph that shows the social support percentage correlated to happiness score in Afghanistan and Albania.

This is important because it shows you how in different countries with different social supports affect the happiness score of countries in a major way 



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




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_14_0.png)
    



**Happiness Scores in Northern European Countries** 

This is a bar graph that shows the happiness score percentage of northern European countries 

This is important because it helps visualize what the northern European countries are experiencing when it comes down to the happiness level of those  countries 



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




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_16_0.png)
    



###### Happiness Scores and Government Trust

This chart displays the happiness scores and government trust percentages of Albania and Finland. Albania has an extremely low percentage of government trust and a fairly low happiness score. Finland has a very high percentage of both government trust and happiness. From this chart, it can be seen that countries who trust their government will be happier.



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




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_18_0.png)
    



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




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_20_0.png)
    



## How your social situation affects your happiness




```python
fig = px.bar(Both_sexes.head(20), x="Country", y="happiness_score", title="Happiness")
fig.update_layout(
    yaxis_title="Happiness",
    )

fig.show()
```




<html>
<head><meta charset="utf-8" /></head>
<body>
    <div>            <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-AMS-MML_SVG"></script><script type="text/javascript">if (window.MathJax) {MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}</script>                <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script src="https://cdn.plot.ly/plotly-2.4.2.min.js"></script>                <div id="48165f22-8d75-468c-bc7f-9e9ee9426ea9" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("48165f22-8d75-468c-bc7f-9e9ee9426ea9")) {                    Plotly.newPlot(                        "48165f22-8d75-468c-bc7f-9e9ee9426ea9",                        [{"alignmentgroup":"True","hovertemplate":"Country=%{x}<br>happiness_score=%{y}<extra></extra>","legendgroup":"","marker":{"color":"#636efa","pattern":{"shape":""}},"name":"","offsetgroup":"","orientation":"v","showlegend":false,"textposition":"auto","type":"bar","x":["Afghanistan","Albania","Algeria","Argentina","Armenia","Australia","Austria","Azerbaijan","Bahrain","Bangladesh","Belarus","Belgium","Benin","Bosnia and Herzegovina","Botswana","Brazil","Bulgaria","Burkina Faso","Burundi","Cambodia"],"xaxis":"x","y":[3.575,4.959,5.605,6.574,4.35,7.284,7.2,5.2120000000000015,5.96,4.694,5.813,6.937,3.34,4.949,4.332,6.983,4.218,3.587,2.905,3.819],"yaxis":"y"}],                        {"barmode":"relative","legend":{"tracegroupgap":0},"template":{"data":{"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"geo":{"bgcolor":"white","lakecolor":"white","landcolor":"#E5ECF6","showlakes":true,"showland":true,"subunitcolor":"white"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"light"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"bgcolor":"#E5ECF6","radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"ternary":{"aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"bgcolor":"#E5ECF6","caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"title":{"x":0.05},"xaxis":{"automargin":true,"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","zerolinewidth":2}}},"title":{"text":"Happiness"},"xaxis":{"anchor":"y","domain":[0.0,1.0],"title":{"text":"Country"}},"yaxis":{"anchor":"x","domain":[0.0,1.0],"title":{"text":"Happiness"}}},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('48165f22-8d75-468c-bc7f-9e9ee9426ea9');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                            </script>        </div>
</body>
</html>



This chart represents the happiness levels per country overall for both sexes. The happiness level does vary from country to country, and they are all very different because of the factors around these countries the differences. 




```python
plt.figure(figsize=(20,10))
g=sns.lineplot(data=merge_data,x="family",y="happiness_score", sort=True)

plt.xlabel("Family")
plt.ylabel("Happiness")
plt.show()
```




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_24_0.png)
    



This chart shows the affect of family and how it boosts the level of happiness. This factor positively affects the level of happiness as the more family increases, the level of happiness does overall as well. Based on this data, if you are feeling unhappy, you should go 
see your family as they increase the levels of happiness.




```python
plt.figure(figsize=(20,10))
g=sns.lineplot(data=merge_data,x="health",y="happiness_score", sort=True)

plt.xlabel("Health")
plt.ylabel("Happiness")
plt.show()
```




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_26_0.png)
    



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




    
![png](Happiness%20across%20countries_files/Happiness%20across%20countries_28_0.png)
    



This graph shows the happiness score for Afghanistan and Albania and the social support percentage. This shows that the more social support people in a country receive the happier that person tends to be. This is why it is important to 
surround yourself with family and friends that will support you.



**Over All Summary** 

Based on the following charts listed above, all of these factors can both negatively and positively affect peoples happiness, and how they feel overall. 

