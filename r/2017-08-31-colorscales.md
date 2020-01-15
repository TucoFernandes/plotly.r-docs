---
name: Colorscales
permalink: r/colorscales/
description: How to create colorscales in R with Plotly.
layout: base
language: r
page_type: u-guide
display_as: file_settings
order: 15
thumbnail: thumbnail/heatmap_colorscale.jpg
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

### Colorscale for Scatter Plots


```r
library(plotly)

p <- plot_ly(
  type = 'scatter',
  mode='markers',
  y=rep(5, 40),
  marker=list(
    size=seq(0, 39),
    color=seq(0, 39),
    colorbar=list(
      title='Colorbar'
    ),
    colorscale='Viridis',
    reversescale =T
  )
  ) %>%
  layout(
    xaxis = list(
      showgrid = F,
      zeroline = F
    ),
    yaxis = list(
      showgrid = F,
      zeroline = F
    )
  )
```

### Colorscale Contour


```r
library(plotly)

p <- plot_ly(
  type = 'contour',
  z=matrix(c(10, 10.625, 12.5, 15.625, 20,
      5.625, 6.25, 8.125, 11.25, 15.625,
      2.5, 3.125, 5., 8.125, 12.5,
      0.625, 1.25, 3.125, 6.25, 10.625,
      0, 0.625, 2.5, 5.625, 10),
      nrow=5, ncol=5)
)

p
```

<div id="htmlwidget-b415e01d1a6e12d5ae15" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-b415e01d1a6e12d5ae15">{"x":{"visdat":{"342c2fe21494":["function () ","plotlyVisDat"]},"cur_data":"342c2fe21494","attrs":{"342c2fe21494":{"z":[[10,5.625,2.5,0.625,0],[10.625,6.25,3.125,1.25,0.625],[12.5,8.125,5,3.125,2.5],[15.625,11.25,8.125,6.25,5.625],[20,15.625,12.5,10.625,10]],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"contour"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"scene":{"zaxis":{"title":[]}},"xaxis":{"domain":[0,1],"automargin":true},"yaxis":{"domain":[0,1],"automargin":true},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5}},"source":"A","config":{"showSendToCloud":false},"data":[{"colorbar":{"title":"","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top"},"colorscale":[["0","rgba(68,1,84,1)"],["0.0416666666666667","rgba(70,19,97,1)"],["0.0833333333333333","rgba(72,32,111,1)"],["0.125","rgba(71,45,122,1)"],["0.166666666666667","rgba(68,58,128,1)"],["0.208333333333333","rgba(64,70,135,1)"],["0.25","rgba(60,82,138,1)"],["0.291666666666667","rgba(56,93,140,1)"],["0.333333333333333","rgba(49,104,142,1)"],["0.375","rgba(46,114,142,1)"],["0.416666666666667","rgba(42,123,142,1)"],["0.458333333333333","rgba(38,133,141,1)"],["0.5","rgba(37,144,140,1)"],["0.541666666666667","rgba(33,154,138,1)"],["0.583333333333333","rgba(39,164,133,1)"],["0.625","rgba(47,174,127,1)"],["0.666666666666667","rgba(53,183,121,1)"],["0.708333333333333","rgba(79,191,110,1)"],["0.75","rgba(98,199,98,1)"],["0.791666666666667","rgba(119,207,85,1)"],["0.833333333333333","rgba(147,214,70,1)"],["0.875","rgba(172,220,52,1)"],["0.916666666666667","rgba(199,225,42,1)"],["0.958333333333333","rgba(226,228,40,1)"],["1","rgba(253,231,37,1)"]],"showscale":true,"z":[[10,5.625,2.5,0.625,0],[10.625,6.25,3.125,1.25,0.625],[12.5,8.125,5,3.125,2.5],[15.625,11.25,8.125,6.25,5.625],[20,15.625,12.5,10.625,10]],"type":"contour","line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Share Color Axis

This example shows how to specify the color scale and color bar per trace. To share colorscale information in multiple subplots, you can use [coloraxis](https://plot.ly/r/reference/#scatter-marker-line-coloraxis).
Below we show how to set a reference coloraxis1 to a shared coloraxis, which are set in the layout. Note that multiple color scales can be linked to the same color.


```r
library(plotly)

p1 <- plot_ly(
    type = "heatmap",
    x = c(1,2,3,4),
    z = list(c(1,2,3,4), c(4,-3,-1,1)),
    coloraxis = 'coloraxis')
p2 <- plot_ly(
    type = "heatmap",
    x = c(3,4,5,6),
    z = list(c(10,2,1,0), c(4,3,5,6)),
    coloraxis = 'coloraxis')
p <- subplot(p1, p2) %>%
  layout(coloraxis=list(colorscale='Jet'))

p
```

<div id="htmlwidget-8e157781b3e427b62f9f" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-8e157781b3e427b62f9f">{"x":{"data":[{"x":[1,2,3,4],"z":[[1,2,3,4],[4,-3,-1,1]],"coloraxis":"coloraxis","type":"heatmap","xaxis":"x","yaxis":"y","frame":null},{"x":[3,4,5,6],"z":[[10,2,1,0],[4,3,5,6]],"coloraxis":"coloraxis","type":"heatmap","xaxis":"x2","yaxis":"y2","frame":null}],"layout":{"xaxis":{"domain":[0,0.48],"automargin":true,"anchor":"y"},"xaxis2":{"domain":[0.52,1],"automargin":true,"anchor":"y2"},"yaxis2":{"domain":[0,1],"automargin":true,"anchor":"x2"},"yaxis":{"domain":[0,1],"automargin":true,"anchor":"x"},"annotations":[],"shapes":[],"images":[],"margin":{"b":40,"l":60,"t":25,"r":10},"scene":{"zaxis":{"title":[]}},"hovermode":"closest","showlegend":true,"coloraxis":{"colorscale":"Jet"}},"attrs":{"342c7b1e3096":{"x":[1,2,3,4],"z":[[1,2,3,4],[4,-3,-1,1]],"coloraxis":"coloraxis","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"heatmap"},"342c2d3b8779":{"x":[3,4,5,6],"z":[[10,2,1,0],[4,3,5,6]],"coloraxis":"coloraxis","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"heatmap"}},"source":"A","config":{"showSendToCloud":false},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"subplot":true,"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plot.ly/r/reference/#heatmap-colorscale](https://plot.ly/r/reference/#heatmap-colorscale) for more information and options!
