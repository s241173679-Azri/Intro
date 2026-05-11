```R
library(qcc)
library(plotly)
library(htmlwidgets)

# Filter data
filtered_data_resistance <- X016[X016$Machine == 1 & X016$Temperature == 303 & X016$Pressure == 100,]
part_resistance_data <- filtered_data_resistance$PartResistance

# Check if there is enough data for the control chart
if (length(part_resistance_data) < 2) {
    stop("Not enough data points after filtering to create a control chart. Need at least 2 points.")
}

# Calculate control chart statistics using qcc (for UCL, LCL, Center)
qcc_obj_resistance <- qcc(part_resistance_data, type="xbar.one", plot=FALSE)
center_line_resistance <- qcc_obj_resistance$center
ucl_resistance <- qcc_obj_resistance$limits[2]
lcl_resistance <- qcc_obj_resistance$limits[1]

# Create a data frame for plotting with plotly
plot_df_resistance <- data.frame(
  observation = 1:length(part_resistance_data),
  value = part_resistance_data,
  center = rep(center_line_resistance, length(part_resistance_data)),
  ucl = rep(ucl_resistance, length(part_resistance_data)),
  lcl = rep(lcl_resistance, length(part_resistance_data))
)

# Create the plotly chart
p_resistance <- plot_ly(plot_df_resistance, x = ~observation, y = ~value, type = 'scatter', mode = 'lines+markers', name = 'Part Resistance',
             marker = list(color = '#0072B2', size = 6), line = list(color = '#0072B2')) %>%
  add_trace(y = ~center, mode = 'lines', name = 'Center Line', line = list(color = 'grey', dash = 'dash'), showlegend = TRUE) %>%
  add_trace(y = ~ucl, mode = 'lines', name = 'UCL', line = list(color = '#D55E00', dash = 'dash'), showlegend = TRUE) %>%
  add_trace(y = ~lcl, mode = 'lines', name = 'LCL', line = list(color = '#D55E00', dash = 'dash'), showlegend = TRUE) %>%
  layout(title = list(text = 'Xbar.one Control Chart for Part Resistance (Machine 1, Temp 303, Pres 100)', font = list(size = 20)),
         xaxis = list(title = list(text = 'Observation', font = list(size = 18)), tickfont = list(size = 14)),
         yaxis = list(title = list(text = 'Part Resistance', font = list(size = 18)), tickfont = list(size = 14)),
         plot_bgcolor = 'white',
         paper_bgcolor = 'white',
         hovermode = 'x unified')

# To save the plot: saveWidget(p_resistance, file = 'xbar_one_chart_resistance.html', selfcontained = TRUE)
# To display the plot: print(p_resistance)
```
