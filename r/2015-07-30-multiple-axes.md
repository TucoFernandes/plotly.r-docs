---
name: Multiple Axes
permalink: r/multiple-axes/
description: How to make a graph with multiple axes in R with Plotly.
layout: base
thumbnail: thumbnail/multiple-axes.jpg
language: r
page_type: example_index
display_as: multiple_axes
order: 1
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

### Multiple Y Axes


```r
library(plotly)
ay <- list(
  tickfont = list(color = "red"),
  overlaying = "y",
  side = "right",
  title = "second y axis"
)
p <- plot_ly() %>%
  add_lines(x = ~1:3, y = ~10*(1:3), name = "slope of 10") %>%
  add_lines(x = ~2:4, y = ~1:3, name = "slope of 1", yaxis = "y2") %>%
  layout(
    title = "Double Y Axis", yaxis2 = ay,
    xaxis = list(title="x")
  )

p
```

<div id="htmlwidget-c7bead8f43b095005586" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c7bead8f43b095005586">{"x":{"visdat":{"2561466a628d":["function () ","plotlyVisDat"]},"cur_data":"2561466a628d","attrs":{"2561466a628d":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":{},"y":{},"type":"scatter","mode":"lines","name":"slope of 10","inherit":true},"2561466a628d.1":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":{},"y":{},"type":"scatter","mode":"lines","name":"slope of 1","yaxis":"y2","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Double Y Axis","yaxis2":{"tickfont":{"color":"red"},"overlaying":"y","side":"right","title":"second y axis"},"xaxis":{"domain":[0,1],"automargin":true,"title":"x"},"yaxis":{"domain":[0,1],"automargin":true,"title":"10 * (1:3)"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[1,2,3],"y":[10,20,30],"type":"scatter","mode":"lines","name":"slope of 10","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[2,3,4],"y":[1,2,3],"type":"scatter","mode":"lines","name":"slope of 1","yaxis":"y2","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_y":{"color":"rgba(255,127,14,1)"},"error_x":{"color":"rgba(255,127,14,1)"},"line":{"color":"rgba(255,127,14,1)"},"xaxis":"x","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
