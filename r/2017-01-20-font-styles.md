---
description: How to create font styles in R with Plotly.
display_as: file_settings
language: r
layout: base
name: Font Styles
order: 11
output:
  html_document:
    keep_md: true
page_type: u-guide
permalink: r/font/
thumbnail: thumbnail/text-and-annotations.png
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

### Global Font Properties


```r
library(plotly)

t <- list(
  family = "sans serif",
  size = 14,
  color = 'blue')

p <- plot_ly(x=c(1,2,3,4,5), y=c(1,2,3,2,1)) %>%
  layout(title="Font Styling",
         font=t)


p
```

<div id="htmlwidget-bc1911e504e659b5a42e" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-bc1911e504e659b5a42e">{"x":{"visdat":{"2fa04990364":["function () ","plotlyVisDat"]},"cur_data":"2fa04990364","attrs":{"2fa04990364":{"x":[1,2,3,4,5],"y":[1,2,3,2,1],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20]}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Font Styling","font":{"family":"sans serif","size":14,"color":"blue"},"xaxis":{"domain":[0,1],"automargin":true,"title":[]},"yaxis":{"domain":[0,1],"automargin":true,"title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[1,2,3,4,5],"y":[1,2,3,2,1],"type":"scatter","mode":"markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plot.ly/r/reference/#layout-font](https://plot.ly/r/reference/#layout-font) for more information and options!
