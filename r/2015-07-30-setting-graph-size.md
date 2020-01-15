---
description: How to change the size of graphs in R.
display_as: file_settings
language: r
layout: base
name: Setting Graph Size
order: 20
output:
  html_document:
    keep_md: true
page_type: u-guide
permalink: r/setting-graph-size/
thumbnail: thumbnail/sizing.png
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

### Customize Margins and Plot Size

```r
library(plotly)
m <- list(
  l = 50,
  r = 50,
  b = 100,
  t = 100,
  pad = 4
)
p <- plot_ly(x = seq(0, 8), y = seq(0, 8)) %>%
  layout(autosize = F, width = 500, height = 500, margin = m)

p
```

<div id="htmlwidget-af35ce95f4283ab28076" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-af35ce95f4283ab28076">{"x":{"visdat":{"26d51d5c378e":["function () ","plotlyVisDat"]},"cur_data":"26d51d5c378e","attrs":{"26d51d5c378e":{"x":[0,1,2,3,4,5,6,7,8],"y":[0,1,2,3,4,5,6,7,8],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20]}},"layout":{"width":500,"height":500,"margin":{"b":100,"l":50,"t":100,"r":50,"pad":4},"autosize":false,"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[0,1,2,3,4,5,6,7,8],"y":[0,1,2,3,4,5,6,7,8],"type":"scatter","mode":"markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Automatically Adjust Margins

```r
library(plotly)
yaxis <- list(
  title = 'Y-axis Title',
  ticktext = list('long label','Very long label','3','label'),
  tickvals = list(1, 2, 3, 4),
  tickmode = "array",
  automargin = TRUE,
  titlefont = list(size=30)
)
p <- plot_ly(x = c('Apples', 'Oranges', 'Watermelon', 'Pears'), y = c(3, 1, 2, 4), width = 500, height = 500, type = 'bar') %>%
  layout(autosize = F, yaxis = yaxis)

p
```

<div id="htmlwidget-69e91b7ea5aaf6d9c2df" style="width:500px;height:500px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-69e91b7ea5aaf6d9c2df">{"x":{"visdat":{"26d56c994f4c":["function () ","plotlyVisDat"]},"cur_data":"26d56c994f4c","attrs":{"26d56c994f4c":{"x":["Apples","Oranges","Watermelon","Pears"],"y":[3,1,2,4],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"}},"layout":{"width":500,"height":500,"margin":{"b":40,"l":60,"t":25,"r":10},"autosize":false,"yaxis":{"domain":[0,1],"automargin":true,"title":"Y-axis Title","ticktext":["long label","Very long label","3","label"],"tickvals":[1,2,3,4],"tickmode":"array","titlefont":{"size":30}},"xaxis":{"domain":[0,1],"automargin":true,"title":[],"type":"category","categoryorder":"array","categoryarray":["Apples","Oranges","Pears","Watermelon"]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["Apples","Oranges","Watermelon","Pears"],"y":[3,1,2,4],"type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
