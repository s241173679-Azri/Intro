```R
library(qcc)
library(plotly)
library(htmlwidgets)

# Filter data
filtered_data <- X016[X016$Machine == 1 & X016$Temperature == 303 & X016$Pressure == 100,]
part_length_data <- filtered_data$PartLength

# Check if there is enough data for the control chart
if (length(part_length_data) < 2) {
    stop("Not enough data points after filtering to create a control chart. Need at least 2 points.")
}

# Calculate control chart statistics using qcc (for UCL, LCL, Center)
qcc_obj <- qcc(part_length_data, type="xbar.one", plot=FALSE)
center_line <- qcc_obj$center
ucl <- qcc_obj$limits[2]
lcl <- qcc_obj$limits[1]

# Create a data frame for plotting with plotly
plot_df <- data.frame(
  observation = 1:length(part_length_data),
  value = part_length_data,
  center = rep(center_line, length(part_length_data)),
  ucl = rep(ucl, length(part_length_data)),
  lcl = rep(lcl, length(part_length_data))
)

# Create the plotly chart
p <- plot_ly(plot_df, x = ~observation, y = ~value, type = 'scatter', mode = 'lines+markers', name = 'Part Length',
             marker = list(color = '#0072B2', size = 6), line = list(color = '#0072B2')) %>%
  add_trace(y = ~center, mode = 'lines', name = 'Center Line', line = list(color = 'grey', dash = 'dash'), showlegend = TRUE) %>%
  add_trace(y = ~ucl, mode = 'lines', name = 'UCL', line = list(color = '#D55E00', dash = 'dash'), showlegend = TRUE) %>%
  add_trace(y = ~lcl, mode = 'lines', name = 'LCL', line = list(color = '#D55E00', dash = 'dash'), showlegend = TRUE) %>%
  layout(title = list(text = 'Xbar.one Control Chart for Part Length (Machine 1, Temp 303, Pres 100)', font = list(size = 20)),
         xaxis = list(title = list(text = 'Observation', font = list(size = 18)), tickfont = list(size = 14)),
         yaxis = list(title = list(text = 'Part Length', font = list(size = 18)), tickfont = list(size = 14)),
         plot_bgcolor = 'white',
         paper_bgcolor = 'white',
         hovermode = 'x unified')

# To save the plot: saveWidget(p, file = 'xbar_one_chart.html', selfcontained = TRUE)
# To display the plot: print(p)
```
