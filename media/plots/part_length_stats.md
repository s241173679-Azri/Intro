```R
# Filter the X016 dataset for the specified conditions
filtered_data_stats <- X016[X016$Machine == 1 & X016$Temperature == 303 & X016$Pressure == 100,]

# Calculate mean, median, and standard deviation of PartLength
mean_partlength <- mean(filtered_data_stats$PartLength)
median_partlength <- median(filtered_data_stats$PartLength)
sd_partlength <- sd(filtered_data_stats$PartLength)

# Print the statistics (or use for further analysis)
cat("\nKey Statistics for PartLength (Machine 1, Temp 303, Pres 100):\n")
cat("------------------------------------------------------------------\n")
cat(paste0("Mean: ", round(mean_partlength, 4), "\n"))
cat(paste0("Median: ", round(median_partlength, 4), "\n"))
cat(paste0("Standard Deviation: ", round(sd_partlength, 4), "\n"))
cat("------------------------------------------------------------------\n")
```
