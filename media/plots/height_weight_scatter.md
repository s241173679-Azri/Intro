```R
library(plotly)
library(htmlwidgets)

p <- plot_ly(bigclass, x = ~height, y = ~weight, color = ~sex,
             colors = c('#0072B2', '#D55E00'),
             type = 'scatter', mode = 'markers',
             marker = list(size = 10, opacity = 0.8))

p <- p %>%
  layout(title = list(text = 'Height vs. Weight by Sex', font = list(size = 20)),
         xaxis = list(title = list(text = 'Height', font = list(size = 18)), tickfont = list(size = 14)),
         yaxis = list(title = list(text = 'Weight', font = list(size = 18)), tickfont = list(size = 14)),
         plot_bgcolor = 'white',
         paper_bgcolor = 'white')

# To save the plot: saveWidget(p, file = 'height_weight_scatter.html', selfcontained = TRUE)
# To display the plot: print(p)
```
