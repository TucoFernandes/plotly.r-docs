---
name: geom_errorbar
permalink: ggplot2/geom_errorbar/
description: Examples of geom_errobar in R and ggplot2
layout: base
thumbnail: thumbnail/error-bar.jpg
language: ggplot2
page_type: example_index
display_as: statistics
order: 2
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

### Basic Error Bar


```r
library(plotly)

df <- data.frame(x = 1:10,
                 y = 1:10,
                 ymin = (1:10) - runif(10),
                 ymax = (1:10) + runif(10),
                 xmin = (1:10) - runif(10),
                 xmax = (1:10) + runif(10))

p <- ggplot(data = df,aes(x = x,y = y)) + 
    geom_point() + 
    geom_errorbar(aes(ymin = ymin,ymax = ymax)) + 
    geom_errorbarh(aes(xmin = xmin,xmax = xmax))

p <- ggplotly(p)

p
```

<div id="htmlwidget-7ab5e91f04027ff2d13b" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-7ab5e91f04027ff2d13b">{"x":{"data":[{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["x:  1<br />y:  1","x:  2<br />y:  2","x:  3<br />y:  3","x:  4<br />y:  4","x:  5<br />y:  5","x:  6<br />y:  6","x:  7<br />y:  7","x:  8<br />y:  8","x:  9<br />y:  9","x: 10<br />y: 10"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["ymin: 0.6650689<br />ymax:  1.652732<br />x:  1<br />y:  1","ymin: 1.8467108<br />ymax:  2.393924<br />x:  2<br />y:  2","ymin: 2.2056242<br />ymax:  3.108465<br />x:  3<br />y:  3","ymin: 3.0568319<br />ymax:  4.992786<br />x:  4<br />y:  4","ymin: 4.2119455<br />ymax:  5.682628<br />x:  5<br />y:  5","ymin: 5.9521806<br />ymax:  6.729815<br />x:  6<br />y:  6","ymin: 6.5780164<br />ymax:  7.230279<br />x:  7<br />y:  7","ymin: 7.9524880<br />ymax:  8.306408<br />x:  8<br />y:  8","ymin: 8.1286236<br />ymax:  9.352266<br />x:  9<br />y:  9","ymin: 9.9522651<br />ymax: 10.752408<br />x: 10<br />y: 10"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_y":{"array":[0.652731839101762,0.393924162955955,0.10846548108384,0.992785556940362,0.682628320995718,0.729815391125157,0.230278881499544,0.306408174568787,0.352266221307218,0.752407814841717],"arrayminus":[0.334931125165895,0.153289220295846,0.794375849422067,0.943168095545843,0.788054508622736,0.0478193655144423,0.421983623411506,0.0475119738839567,0.871376355877146,0.0477348733693361],"type":"data","width":17.9822583494171,"symmetric":false,"color":"rgba(0,0,0,1)"},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["xmin: 0.2581362<br />xmax:  1.106595<br />x:  1<br />y:  1","xmin: 1.5272127<br />xmax:  2.248673<br />x:  2<br />y:  2","xmin: 2.6868760<br />xmax:  3.396485<br />x:  3<br />y:  3","xmin: 3.7796797<br />xmax:  4.413819<br />x:  4<br />y:  4","xmin: 4.6690669<br />xmax:  5.383147<br />x:  5<br />y:  5","xmin: 5.4201276<br />xmax:  6.960670<br />x:  6<br />y:  6","xmin: 6.2066568<br />xmax:  7.494864<br />x:  7<br />y:  7","xmin: 7.4915924<br />xmax:  8.823409<br />x:  8<br />y:  8","xmin: 8.1873232<br />xmax:  9.250657<br />x:  9<br />y:  9","xmin: 9.8560872<br />xmax: 10.041385<br />x: 10<br />y: 10"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_x":{"array":[0.106595340417698,0.248672807123512,0.396485150326043,0.413819195702672,0.38314677006565,0.960670127999038,0.494863728992641,0.823408864904195,0.250656722811982,0.0413848613388836],"arrayminus":[0.741863764356822,0.472787277307361,0.313123964937404,0.220320277148858,0.330933134071529,0.579872379545122,0.793343248544261,0.508407562738284,0.81267680414021,0.143912826664746],"type":"data","width":12.8311956633074,"symmetric":false,"color":"rgba(0,0,0,1)"},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":31.4155251141553},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-0.251456952574663,10.9595931882178],"tickmode":"array","ticktext":["0.0","2.5","5.0","7.5","10.0"],"tickvals":[0,2.5,5,7.5,10],"categoryorder":"array","categoryarray":["0.0","2.5","5.0","7.5","10.0"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"x","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.0398796092579142,11.2625282055838],"tickmode":"array","ticktext":["3","6","9"],"tickvals":[3,6,9],"categoryorder":"array","categoryarray":["3","6","9"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"y","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"44236d76e06e":{"x":{},"y":{},"type":"scatter"},"44235db2e5ae":{"ymin":{},"ymax":{},"x":{},"y":{}},"4423133fc1d4":{"xmin":{},"xmax":{},"x":{},"y":{}}},"cur_data":"44236d76e06e","visdat":{"44236d76e06e":["function (y) ","x"],"44235db2e5ae":["function (y) ","x"],"4423133fc1d4":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Margin Error Bar


```r
library(plotly)

population <- data.frame(Year=seq(1790, 1970, length.out=length(uspop)), 
                         Population=uspop, 
                         Error=rnorm(length(uspop), 5))

library(ggplot2)
p <- ggplot(population, aes(x=Year, y=Population, 
                       ymin=Population-Error, ymax=Population+Error))+
  geom_line()+
  geom_point(pch=2)+
  geom_errorbar(width=0.9)

p <- ggplotly(p)

p
```

<div id="htmlwidget-c3f0da3fd9acb5845ee5" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c3f0da3fd9acb5845ee5">{"x":{"data":[{"x":[1790,1800,1810,1820,1830,1840,1850,1860,1870,1880,1890,1900,1910,1920,1930,1940,1950,1960,1970],"y":[3.93,5.31,7.24,9.64,12.9,17.1,23.2,31.4,39.8,50.2,62.9,76,92,105.7,122.8,131.7,151.3,179.3,203.2],"text":["Year: 1790<br />Population:   3.93<br />Population - Error:  -0.7768081<br />Population + Error:   8.636808","Year: 1800<br />Population:   5.31<br />Population - Error:  -0.1019677<br />Population + Error:  10.721968","Year: 1810<br />Population:   7.24<br />Population - Error:   2.4369315<br />Population + Error:  12.043068","Year: 1820<br />Population:   9.64<br />Population - Error:   3.2354967<br />Population + Error:  16.044503","Year: 1830<br />Population:  12.90<br />Population - Error:   7.4890288<br />Population + Error:  18.310971","Year: 1840<br />Population:  17.10<br />Population - Error:   9.8631577<br />Population + Error:  24.336842","Year: 1850<br />Population:  23.20<br />Population - Error:  19.1802031<br />Population + Error:  27.219797","Year: 1860<br />Population:  31.40<br />Population - Error:  25.8455726<br />Population + Error:  36.954427","Year: 1870<br />Population:  39.80<br />Population - Error:  34.7930709<br />Population + Error:  44.806929","Year: 1880<br />Population:  50.20<br />Population - Error:  44.7400437<br />Population + Error:  55.659956","Year: 1890<br />Population:  62.90<br />Population - Error:  59.3314039<br />Population + Error:  66.468596","Year: 1900<br />Population:  76.00<br />Population - Error:  71.6653066<br />Population + Error:  80.334693","Year: 1910<br />Population:  92.00<br />Population - Error:  85.7541988<br />Population + Error:  98.245801","Year: 1920<br />Population: 105.70<br />Population - Error: 101.3099621<br />Population + Error: 110.090038","Year: 1930<br />Population: 122.80<br />Population - Error: 117.2883322<br />Population + Error: 128.311668","Year: 1940<br />Population: 131.70<br />Population - Error: 126.8289305<br />Population + Error: 136.571070","Year: 1950<br />Population: 151.30<br />Population - Error: 146.5730996<br />Population + Error: 156.026900","Year: 1960<br />Population: 179.30<br />Population - Error: 176.7864399<br />Population + Error: 181.813560","Year: 1970<br />Population: 203.20<br />Population - Error: 198.0316681<br />Population + Error: 208.368332"],"type":"scatter","mode":"lines+markers","line":{"width":1.88976377952756,"color":"transparent","dash":"solid"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"triangle-up-open","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"opacity":1,"error_y":{"array":[4.70680805955496,5.41196772681226,4.80306849628512,6.40450326878461,5.41097122111892,7.23684232874211,4.01979686925266,5.55442741069576,5.00692914715546,5.45995631969055,3.56859608056757,4.33469336084664,6.24580117626076,4.39003789119103,5.51166780906674,4.8710695420522,4.72690035255513,2.51356008449594,5.16833191182548],"arrayminus":[4.70680805955496,5.41196772681226,4.80306849628512,6.40450326878461,5.41097122111892,7.23684232874211,4.01979686925266,5.55442741069576,5.00692914715546,5.45995631969055,3.56859608056757,4.33469336084664,6.24580117626076,4.39003789119103,5.51166780906674,4.87106954205218,4.72690035255513,2.51356008449594,5.16833191182548],"type":"data","width":1.01311623699693,"symmetric":false,"color":"rgba(0,0,0,1)"},"frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":43.1050228310502},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[1780.505,1979.495],"tickmode":"array","ticktext":["1800","1850","1900","1950"],"tickvals":[1800,1850,1900,1950],"categoryorder":"array","categoryarray":["1800","1850","1900","1950"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"Year","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-11.234065058124,218.825588910394],"tickmode":"array","ticktext":["0","50","100","150","200"],"tickvals":[0,50,100,150,200],"categoryorder":"array","categoryarray":["0","50","100","150","200"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Population","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","showSendToCloud":false},"source":"A","attrs":{"442377d7d971":{"x":{},"y":{},"ymin":{},"ymax":{},"type":"scatter"},"442325431638":{"x":{},"y":{},"ymin":{},"ymax":{}},"44231a19d3a4":{"x":{},"y":{},"ymin":{},"ymax":{}}},"cur_data":"442377d7d971","visdat":{"442377d7d971":["function (y) ","x"],"442325431638":["function (y) ","x"],"44231a19d3a4":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
