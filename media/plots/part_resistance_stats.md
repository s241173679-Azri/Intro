```R
# Filter the X016 dataset for the specified conditions
filtered_data_resistance_stats <- X016[X016$Machine == 1 & X016$Temperature == 303 & X016$Pressure == 100,]

# Calculate mean, median, and standard deviation of PartResistance
mean_partresistance <- mean(filtered_data_resistance_stats$PartResistance)
median_partresistance <- median(filtered_data_resistance_stats$PartResistance)
sd_partresistance <- sd(filtered_data_resistance_stats$PartResistance)

# Print the statistics (or use for further analysis)
cat("\nKey Statistics for PartResistance (Machine 1, Temp 303, Pres 100):\n")
cat("------------------------------------------------------------------\n")
cat(paste0("Mean: ", round(mean_partresistance, 4), "\n"))
cat(paste0("Median: ", round(median_partresistance, 4), "\n"))
cat(paste0("Standard Deviation: ", round(sd_partresistance, 4), "\n"))
cat("------------------------------------------------------------------\n")
```
