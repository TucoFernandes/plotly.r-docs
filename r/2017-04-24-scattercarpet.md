---
description: How to create carpet plots in R with Plotly.
display_as: scientific
language: r
layout: base
name: Carpet Scatter Plot
order: 9
output:
  html_document:
    keep_md: true
permalink: r/carpet-scatter/
thumbnail: thumbnail/scattercarpet.jpg
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

### Basic Carpet Plot


```r
library(plotly)

p <- plot_ly(
    type = 'carpet',
    a = c(4, 4, 4, 4.5, 4.5, 4.5, 5, 5, 5, 6, 6, 6),
    b = c(1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3),
    y = c(2, 3.5, 4, 3, 4.5, 5, 5.5, 6.5, 7.5, 8, 8.5, 10),
    aaxis = list(
      tickprefix = 'a = ',
      ticksuffix = 'm',
      smoothing = 1,
      minorgridcount = 9
      ),
    baxis = list(
      tickprefix = 'b = ',
      ticksuffix = 'Pa',
      smoothing = 1,
      minorgridcount = 9
      )
    )

p
```

<div id="htmlwidget-10672c3efe884ee9af1a" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-10672c3efe884ee9af1a">{"x":{"visdat":{"32661d18b688":["function () ","plotlyVisDat"]},"cur_data":"32661d18b688","attrs":{"32661d18b688":{"a":[4,4,4,4.5,4.5,4.5,5,5,5,6,6,6],"b":[1,2,3,1,2,3,1,2,3,1,2,3],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"carpet"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"aaxis":{"domain":[0,1],"automargin":true},"baxis":{"domain":[0,1],"automargin":true},"xaxis":{"domain":[0,1],"automargin":true},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"a":[4,4,4,4.5,4.5,4.5,5,5,5,6,6,6],"b":[1,2,3,1,2,3,1,2,3,1,2,3],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"type":"carpet","xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Add Carpet Scatter Trace


```r
library(plotly)

p <- plot_ly(
    type = 'carpet',
    a = c(4, 4, 4, 4.5, 4.5, 4.5, 5, 5, 5, 6, 6, 6),
    b = c(1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3),
    y = c(2, 3.5, 4, 3, 4.5, 5, 5.5, 6.5, 7.5, 8, 8.5, 10),
    aaxis = list(
      tickprefix = 'a = ',
      ticksuffix = 'm',
      smoothing = 1,
      minorgridcount = 9
      ),
    baxis = list(
      tickprefix = 'b = ',
      ticksuffix = 'Pa',
      smoothing = 1,
      minorgridcount = 9
      )
    ) %>%
  add_trace(
    type = 'scattercarpet',
    a = c(4, 4.5, 5, 6),
    b = c(2.5, 2.5, 2.5, 2.5),
    line = list(
      shape = 'spline',
      smoothing = 1,
      color = 'blue'
    ),
    marker = list(color = "blue")
  )

p
```

<div id="htmlwidget-940e20d580a940f93022" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-940e20d580a940f93022">{"x":{"visdat":{"32664df94a24":["function () ","plotlyVisDat"]},"cur_data":"32664df94a24","attrs":{"32664df94a24":{"a":[4,4,4,4.5,4.5,4.5,5,5,5,6,6,6],"b":[1,2,3,1,2,3,1,2,3,1,2,3],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"carpet"},"32664df94a24.1":{"a":[4,4.5,5,6],"b":[2.5,2.5,2.5,2.5],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattercarpet","line":{"shape":"spline","smoothing":1,"color":"blue"},"marker":{"color":"blue"},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"aaxis":{"domain":[0,1],"automargin":true},"baxis":{"domain":[0,1],"automargin":true},"xaxis":{"domain":[0,1],"automargin":true},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"a":[4,4,4,4.5,4.5,4.5,5,5,5,6,6,6],"b":[1,2,3,1,2,3,1,2,3,1,2,3],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"type":"carpet","xaxis":"x","yaxis":"y","frame":null},{"a":[4,4.5,5,6],"b":[2.5,2.5,2.5,2.5],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"type":"scattercarpet","line":{"color":"blue","shape":"spline","smoothing":1},"marker":{"color":"blue","line":{"color":"rgba(255,127,14,1)"}},"mode":"markers+lines","xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>


### Adding Multiple Traces


```r
library(plotly)

p <- plot_ly() %>%
  add_trace(
    type = 'carpet',
    a = c(4, 4, 4, 4.5, 4.5, 4.5, 5, 5, 5, 6, 6, 6),
    b = c(1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3),
    y = c(2, 3.5, 4, 3, 4.5, 5, 5.5, 6.5, 7.5, 8, 8.5, 10),
    aaxis = list(
      tickprefix = 'a = ',
      ticksuffix = 'm',
      smoothing = 1,
      minorgridcount = 9
    ),
    baxis = list(
      tickprefix = 'b = ',
      ticksuffix = 'Pa',
      smoothing = 1,
      minorgridcount = 9
    )
  ) %>%
  add_trace(
    type = 'scattercarpet',
    a = c(4, 4.5, 5, 6),
    b = c(2.5, 2.5, 2.5, 2.5),
    mode = 'markers+lines',
    line = list(
      shape = 'spline',
      smoothing = 1,
      color = "blue"
    ),
    marker = list(color = "blue")
  ) %>%
  add_trace(
    type = 'scattercarpet',
    a = c(4, 4.5, 5, 6),
    b = c(1.5, 1.5, 1.5, 1.5),
    mode = 'lines',
    line = list(
      shape = 'spline',
      smoothing = 1,
      color = "green"
    )
  ) %>%
  add_trace(
    type = 'scattercarpet',
    a = c(5, 5, 5, 5),
    b = c(1, 1.5, 2, 3),
    mode = 'markers',
    marker = list(
      color = "red",
      size = c(0,0,20,0)
    )
  ) %>%
  add_trace(
    type = 'scattercarpet',
    a = c(4.5, 4.5, 4.5, 4.5),
    b = c(1, 1.5, 2, 3),
    mode = 'markers',
    marker = list(
      color = "black",
      size = c(0,0,30,0)
    )
  )

p
```

<div id="htmlwidget-231fc6645204dc1d72f6" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-231fc6645204dc1d72f6">{"x":{"visdat":{"32661da50c9c":["function () ","plotlyVisDat"]},"cur_data":"32661da50c9c","attrs":{"32661da50c9c":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"carpet","a":[4,4,4,4.5,4.5,4.5,5,5,5,6,6,6],"b":[1,2,3,1,2,3,1,2,3,1,2,3],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"inherit":true},"32661da50c9c.1":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattercarpet","a":[4,4.5,5,6],"b":[2.5,2.5,2.5,2.5],"mode":"markers+lines","line":{"shape":"spline","smoothing":1,"color":"blue"},"marker":{"color":"blue"},"inherit":true},"32661da50c9c.2":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattercarpet","a":[4,4.5,5,6],"b":[1.5,1.5,1.5,1.5],"mode":"lines","line":{"shape":"spline","smoothing":1,"color":"green"},"inherit":true},"32661da50c9c.3":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattercarpet","a":[5,5,5,5],"b":[1,1.5,2,3],"mode":"markers","marker":{"color":"red","size":[0,0,20,0]},"inherit":true},"32661da50c9c.4":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scattercarpet","a":[4.5,4.5,4.5,4.5],"b":[1,1.5,2,3],"mode":"markers","marker":{"color":"black","size":[0,0,30,0]},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"aaxis":{"domain":[0,1],"automargin":true},"baxis":{"domain":[0,1],"automargin":true},"xaxis":{"domain":[0,1],"automargin":true},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"type":"carpet","a":[4,4,4,4.5,4.5,4.5,5,5,5,6,6,6],"b":[1,2,3,1,2,3,1,2,3,1,2,3],"y":[2,3.5,4,3,4.5,5,5.5,6.5,7.5,8,8.5,10],"aaxis":{"tickprefix":"a = ","ticksuffix":"m","smoothing":1,"minorgridcount":9},"baxis":{"tickprefix":"b = ","ticksuffix":"Pa","smoothing":1,"minorgridcount":9},"xaxis":"x","yaxis":"y","frame":null},{"type":"scattercarpet","a":[4,4.5,5,6],"b":[2.5,2.5,2.5,2.5],"mode":"markers+lines","line":{"color":"blue","shape":"spline","smoothing":1},"marker":{"color":"blue","line":{"color":"rgba(255,127,14,1)"}},"xaxis":"x","yaxis":"y","frame":null},{"type":"scattercarpet","a":[4,4.5,5,6],"b":[1.5,1.5,1.5,1.5],"mode":"lines","line":{"color":"green","shape":"spline","smoothing":1},"marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(44,160,44,1)"}},"xaxis":"x","yaxis":"y","frame":null},{"type":"scattercarpet","a":[5,5,5,5],"b":[1,1.5,2,3],"mode":"markers","marker":{"color":"red","size":[0,0,20,0],"line":{"color":"rgba(214,39,40,1)"}},"line":{"color":"rgba(214,39,40,1)"},"xaxis":"x","yaxis":"y","frame":null},{"type":"scattercarpet","a":[4.5,4.5,4.5,4.5],"b":[1,1.5,2,3],"mode":"markers","marker":{"color":"black","size":[0,0,30,0],"line":{"color":"rgba(148,103,189,1)"}},"line":{"color":"rgba(148,103,189,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plot.ly/r/reference/#scattercarpet](https://plot.ly/r/reference/#scattercarpet) for more information and options!
