---
name: Pie Charts
permalink: r/pie-charts/
description: How to make pie charts in R using plotly.
layout: base
thumbnail: thumbnail/pie-chart.jpg
language: r
page_type: example_index
display_as: basic
order: 4
output:
  html_document:
    keep_md: true
---



### New to Plotly?

Plotly's R library is free and open source!<br>
[Get started](https://plot.ly/r/getting-started/) by downloading the client and [reading the primer](https://plot.ly/r/getting-started/).<br>
You can set up Plotly to work in [online](https://plot.ly/r/getting-started/#hosting-graphs-in-your-online-plotly-account) or [offline](https://plot.ly/r/offline/) mode.<br>
We also have a quick-reference [cheatsheet](https://images.plot.ly/plotly-documentation/images/r_cheat_sheet.pdf) (new!) to help you get started!

### Version Check

Version 4 of Plotly's R package is now [available](https://plot.ly/r/getting-started/#installation)!<br>
Check out [this post](http://moderndata.plot.ly/upgrading-to-plotly-4-0-and-above/) for more information on breaking changes and new features available in this version.

```r
library(plotly)
packageVersion('plotly')
```

```
## [1] '4.9.1'
```

### Basic Pie Chart


```r
library(plotly)

USPersonalExpenditure <- data.frame("Categorie"=rownames(USPersonalExpenditure), USPersonalExpenditure)
data <- USPersonalExpenditure[,c('Categorie', 'X1960')]

p <- plot_ly(data, labels = ~Categorie, values = ~X1960, type = 'pie') %>%
  layout(title = 'United States Personal Expenditures by Categories in 1960',
         xaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE),
         yaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE))

p
```

<div id="htmlwidget-e0565a120648274d7683" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e0565a120648274d7683">{"x":{"visdat":{"2854e1c4b07":["function () ","plotlyVisDat"]},"cur_data":"2854e1c4b07","attrs":{"2854e1c4b07":{"labels":{},"values":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"pie"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"United States Personal Expenditures by Categories in 1960","xaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"yaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"labels":["Food and Tobacco","Household Operation","Medical and Health","Personal Care","Private Education"],"values":[86.8,46.2,21.1,5.4,3.64],"type":"pie","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Styled Pie Chart


```r
library(plotly)

USPersonalExpenditure <- data.frame("Categorie" = rownames(USPersonalExpenditure), USPersonalExpenditure)
data <- USPersonalExpenditure[, c('Categorie', 'X1960')]

colors <- c('rgb(211,94,96)', 'rgb(128,133,133)', 'rgb(144,103,167)', 'rgb(171,104,87)', 'rgb(114,147,203)')

p <- plot_ly(data, labels = ~Categorie, values = ~X1960, type = 'pie',
        textposition = 'inside',
        textinfo = 'label+percent',
        insidetextfont = list(color = '#FFFFFF'),
        hoverinfo = 'text',
        text = ~paste('$', X1960, ' billions'),
        marker = list(colors = colors,
                      line = list(color = '#FFFFFF', width = 1)),
                      #The 'pull' attribute can also be used to create space between the sectors
        showlegend = FALSE) %>%
  layout(title = 'United States Personal Expenditures by Categories in 1960',
         xaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE),
         yaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE))

p
```

<div id="htmlwidget-04fa208f212e877b81d1" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-04fa208f212e877b81d1">{"x":{"visdat":{"285468f65478":["function () ","plotlyVisDat"]},"cur_data":"285468f65478","attrs":{"285468f65478":{"labels":{},"values":{},"textposition":"inside","textinfo":"label+percent","insidetextfont":{"color":"#FFFFFF"},"hoverinfo":"text","text":{},"marker":{"colors":["rgb(211,94,96)","rgb(128,133,133)","rgb(144,103,167)","rgb(171,104,87)","rgb(114,147,203)"],"line":{"color":"#FFFFFF","width":1}},"showlegend":false,"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"pie"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"United States Personal Expenditures by Categories in 1960","xaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"yaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"labels":["Food and Tobacco","Household Operation","Medical and Health","Personal Care","Private Education"],"values":[86.8,46.2,21.1,5.4,3.64],"textposition":["inside","inside","inside","inside","inside"],"textinfo":"label+percent","insidetextfont":{"color":"#FFFFFF"},"hoverinfo":["text","text","text","text","text"],"text":["$ 86.8  billions","$ 46.2  billions","$ 21.1  billions","$ 5.4  billions","$ 3.64  billions"],"marker":{"color":"rgba(31,119,180,1)","colors":["rgb(211,94,96)","rgb(128,133,133)","rgb(144,103,167)","rgb(171,104,87)","rgb(114,147,203)"],"line":{"color":"#FFFFFF","width":1}},"showlegend":false,"type":"pie","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Subplots
In order to create pie chart subplots, you need to use the [domain](https://plot.ly/javascript/reference/#pie-domain) attribute. It is important to note that the `X` array set the horizontal position whilst the `Y` array sets the vertical. For example, `x=[0,0.5], y=[0, 0.5]` would mean the bottom left position of the plot.

```r
library(plotly)
library(dplyr)

p <- plot_ly() %>%
  add_pie(data = count(diamonds, cut), labels = ~cut, values = ~n,
          name = "Cut", domain = list(x = c(0, 0.4), y = c(0.4, 1))) %>%
  add_pie(data = count(diamonds, color), labels = ~color, values = ~n,
          name = "Color", domain = list(x = c(0.6, 1), y = c(0.4, 1))) %>%
  add_pie(data = count(diamonds, clarity), labels = ~clarity, values = ~n,
          name = "Clarity", domain = list(x = c(0.25, 0.75), y = c(0, 0.6))) %>%
  layout(title = "Pie Charts with Subplots", showlegend = F,
         xaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE),
         yaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE))

p
```

<div id="htmlwidget-031834f6ac46a6f31626" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-031834f6ac46a6f31626">{"x":{"visdat":{"28545d72d54":["function () ","plotlyVisDat"],"28543db1b78a":["function () ","data"],"28544a01272a":["function () ","data"],"28544377d551":["function () ","data"]},"cur_data":"28544377d551","attrs":{"28543db1b78a":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Cut","domain":{"x":[0,0.4],"y":[0.4,1]},"inherit":true},"28544a01272a":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Color","domain":{"x":[0.6,1],"y":[0.4,1]},"inherit":true},"28544377d551":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Clarity","domain":{"x":[0.25,0.75],"y":[0,0.6]},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Pie Charts with Subplots","showlegend":false,"xaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"yaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"values":[1610,4906,12082,13791,21551],"labels":["Fair","Good","Very Good","Premium","Ideal"],"type":"pie","name":"Cut","domain":{"x":[0,0.4],"y":[0.4,1]},"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null},{"values":[6775,9797,9542,11292,8304,5422,2808],"labels":["D","E","F","G","H","I","J"],"type":"pie","name":"Color","domain":{"x":[0.6,1],"y":[0.4,1]},"marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null},{"values":[741,9194,13065,12258,8171,5066,3655,1790],"labels":["I1","SI2","SI1","VS2","VS1","VVS2","VVS1","IF"],"type":"pie","name":"Clarity","domain":{"x":[0.25,0.75],"y":[0,0.6]},"marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Subplots Using Grid
This example uses a plotly [grid](https://plot.ly/javascript/reference/#layout-grid) attribute for the suplots. Reference the row and column destination using the [domain](https://plot.ly/javascript/reference/#pie-domain) attribute.

```r
library(plotly)
library(dplyr)

p <- plot_ly() %>%
  add_pie(data = count(diamonds, cut), labels = ~cut, values = ~n,
          name = "Cut", domain = list(row = 0, column = 0)) %>%
  add_pie(data = count(diamonds, color), labels = ~color, values = ~n,
          name = "Color", domain = list(row = 0, column = 1)) %>%
  add_pie(data = count(diamonds, clarity), labels = ~clarity, values = ~n,
          name = "Clarity", domain = list(row = 1, column = 0)) %>%
  add_pie(data = count(diamonds, cut), labels = ~cut, values = ~n,
          name = "Clarity", domain = list(row = 1, column = 1)) %>%
  layout(title = "Pie Charts with Subplots", showlegend = F,
         grid=list(rows=2, columns=2),
         xaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE),
         yaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE))

p
```

<div id="htmlwidget-c9bd0ac064f7e9610356" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c9bd0ac064f7e9610356">{"x":{"visdat":{"285475d44bf6":["function () ","plotlyVisDat"],"28544227fb53":["function () ","data"],"2854180bb2c":["function () ","data"],"285461929802":["function () ","data"],"28542f622963":["function () ","data"]},"cur_data":"28542f622963","attrs":{"28544227fb53":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Cut","domain":{"row":0,"column":0},"inherit":true},"2854180bb2c":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Color","domain":{"row":0,"column":1},"inherit":true},"285461929802":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Clarity","domain":{"row":1,"column":0},"inherit":true},"28542f622963":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Clarity","domain":{"row":1,"column":1},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Pie Charts with Subplots","showlegend":false,"grid":{"rows":2,"columns":2},"xaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"yaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"values":[1610,4906,12082,13791,21551],"labels":["Fair","Good","Very Good","Premium","Ideal"],"type":"pie","name":"Cut","domain":{"row":0,"column":0},"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null},{"values":[6775,9797,9542,11292,8304,5422,2808],"labels":["D","E","F","G","H","I","J"],"type":"pie","name":"Color","domain":{"row":0,"column":1},"marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null},{"values":[741,9194,13065,12258,8171,5066,3655,1790],"labels":["I1","SI2","SI1","VS2","VS1","VVS2","VVS1","IF"],"type":"pie","name":"Clarity","domain":{"row":1,"column":0},"marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null},{"values":[1610,4906,12082,13791,21551],"labels":["Fair","Good","Very Good","Premium","Ideal"],"type":"pie","name":"Clarity","domain":{"row":1,"column":1},"marker":{"color":"rgba(214,39,40,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

See more examples of subplots [here](https://plot.ly/r/subplots/).

### Donut Chart


```r
library(plotly)

# Get Manufacturer
mtcars$manuf <- sapply(strsplit(rownames(mtcars), " "), "[[", 1)

p <- mtcars %>%
  group_by(manuf) %>%
  summarize(count = n()) %>%
  plot_ly(labels = ~manuf, values = ~count) %>%
  add_pie(hole = 0.6) %>%
  layout(title = "Donut charts using Plotly",  showlegend = F,
         xaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE),
         yaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE))

p
```

<div id="htmlwidget-cecb8cdb84367d5bc120" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-cecb8cdb84367d5bc120">{"x":{"visdat":{"2854516988f2":["function () ","plotlyVisDat"]},"cur_data":"2854516988f2","attrs":{"2854516988f2":{"labels":{},"values":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"pie","hole":0.6,"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Donut charts using Plotly","showlegend":false,"xaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"yaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"labels":["AMC","Cadillac","Camaro","Chrysler","Datsun","Dodge","Duster","Ferrari","Fiat","Ford","Honda","Hornet","Lincoln","Lotus","Maserati","Mazda","Merc","Pontiac","Porsche","Toyota","Valiant","Volvo"],"values":[1,1,1,1,1,1,1,1,2,1,1,2,1,1,1,2,7,1,1,2,1,1],"type":"pie","hole":0.6,"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plot.ly/r/reference/#pie](https://plot.ly/r/reference/#pie) for more information and chart attribute options!
