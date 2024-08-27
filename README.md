# ConfidenceIntervalAnalyzer

**`ConfidenceIntervalAnalyzer`** is a Python program designed for advanced statistical analysis of data samples. It performs normality tests, calculates confidence intervals for the mean or median based on data distribution, and provides graphical visualizations of the results. This program is ideal for statistical analysis and providing detailed insights into data distribution.

## Features

- **Normality Tests:**
  - **Shapiro-Wilk Test:** Assesses if the data follows a normal distribution.
  - **Kolmogorov-Smirnov Test:** Compares the sample distribution to a normal distribution.

- **Data Distribution Visualization:**
  - **Histogram with KDE:** Displays the distribution of data and its density estimation.
  - **Q-Q Plot:** Compares the quantiles of the sample data against a normal distribution.

- **Confidence Interval Calculation:**
  - **For the Mean:** If the data is normally distributed, calculates the confidence interval for the sample mean.
  - **For the Median:** If the data is not normally distributed, calculates the confidence interval for the median using percentiles.

- **Quantification of Points Outside the Confidence Interval:**
  - Counts and calculates the proportion of data points outside the confidence intervals for the mean or median.

## Usage

1. **Prepare the Data:**
   - Replace the sample data provided in the code with your own dataset.

2. **Set Confidence Level:**
   - Modify the `conf_interval` variable to set the desired confidence level (e.g., `0.95` for a 95% confidence level).

3. **Run the Code:**
   - Execute the program to perform normality tests, calculate confidence intervals, and generate graphical visualizations.

4. **Interpret the Results:**
   - Examine the console output to see the results of normality tests, mean or median, and confidence intervals.
   - Analyze the generated plots to visualize data distribution and confidence intervals.

## Statistical Methods

- **Normality Tests:**
  - **Shapiro-Wilk Test:**
    - **Formula:** \( W = \frac{S^2}{\sigma^2} \)
    - **p-value Interpretation:** A p-value > 0.05 suggests that the data is normally distributed.
  - **Kolmogorov-Smirnov Test:**
    - **Formula:** \( D = \sup_{x} |F_n(x) - F(x)| \)
    - **p-value Interpretation:** A p-value > 0.05 suggests that the data follows a normal distribution.

- **Confidence Interval Calculation:**
  - **For the Mean (Normal Distribution):**
    - **Formula:** \( \text{CI} = \bar{x} \pm t_{\alpha/2, n-1} \times \frac{s}{\sqrt{n}} \)
  - **For the Median (Non-Normal Distribution):**
    - **Formula:** Based on percentiles for the specified confidence level.

- **Proportion of Data Points Outside the Confidence Interval:**
  - **Formula:** \( \text{Proportion} = \frac{\text{Number of Points Outside}}{\text{Total Number of Points}} \times 100 \% \)

## Variable Definitions

- **`sample`**: Array of data points used for analysis. Example: `[181.15, 181.22, 181.19, 181.40, 181.14, 181.57, 181.97, 182.04, 182.18]`.

- **`mean`**: The average value of the sample data.

- **`std_dev`**: The sample standard deviation, a measure of the variation of data points.

- **`n`**: The number of data points in the sample.

- **`error_std`**: The standard error of the mean, which measures how much the sample mean is expected to vary from the true population mean.

- **`conf_interval`**: Confidence level for which the interval is calculated, e.g., 0.99 for a 99% confidence interval.

- **`t_critical`**: The critical value from the t-distribution used to calculate the margin of error for the confidence interval of the mean.

- **`margin_of_error_mean`**: The range within which the true mean of the population is expected to lie with the specified confidence level.

- **`lower_bound_mean`**: The lower limit of the confidence interval for the mean.

- **`upper_bound_mean`**: The upper limit of the confidence interval for the mean.

- **`median`**: The middle value of the sample data when arranged in ascending order.

- **`lower_percentile`**: The lower percentile used to calculate the confidence interval for the median.

- **`upper_percentile`**: The upper percentile used to calculate the confidence interval for the median.

- **`lower_bound_median`**: The lower limit of the confidence interval for the median.

- **`upper_bound_median`**: The upper limit of the confidence interval for the median.

- **`outside_conf_interval_mean`**: The count of data points falling outside the confidence interval for the mean.

- **`proportion_outside_mean`**: The percentage of data points falling outside the confidence interval for the mean.

- **`outside_conf_interval_median`**: The count of data points falling outside the confidence interval for the median.

- **`proportion_outside_median`**: The percentage of data points falling outside the confidence interval for the median.

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

---

Feel free to modify the text or add any additional details that may be relevant for your specific use case!
