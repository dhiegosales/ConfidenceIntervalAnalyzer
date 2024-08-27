import numpy as np
import scipy.stats as stats
import matplotlib.pyplot as plt
import seaborn as sns

#User optins
# Data
sample = np.array([181.15, 181.22, 181.19, 181.40, 181.14, 181.57, 181.97, 182.04, 182.18])
# User input for confidence level (e.g., 0.95 for 95%):
conf_interval = 0.99



# Test for Normality
_, p_value_shapiro = stats.shapiro(sample)
_, p_value_ks = stats.kstest(sample, 'norm', args=(np.mean(sample), np.std(sample, ddof=1)))

# Print Normality Test Results
print(f"Shapiro-Wilk test p-value: {p_value_shapiro:.4f}")
print(f"Kolmogorov-Smirnov test p-value: {p_value_ks:.4f}")

# Visualize data distribution and normality
plt.figure(figsize=(14, 6))

# Histogram and Q-Q plot
plt.subplot(1, 2, 1)
sns.histplot(sample, kde=True, color='blue')
plt.title('Histogram and KDE')
plt.xlabel('Value (km²)')
plt.ylabel('Frequency')

plt.subplot(1, 2, 2)
stats.probplot(sample, dist="norm", plot=plt)
plt.title('Q-Q Plot')
plt.xlabel('Theoretical Quantiles')
plt.ylabel('Sample Quantiles')

plt.tight_layout()
plt.show()

# Decision and Plotting
if p_value_shapiro > 0.05 and p_value_ks > 0.05:
    print("The data appears to be normally distributed. Confidence Interval for Mean may be appropriate.")
    
    # Calculate and plot Confidence Interval for Mean
    mean = np.mean(sample)
    std_dev = np.std(sample, ddof=1)
    n = len(sample)
    error_std = std_dev / np.sqrt(n)
    
    # Confidence Interval Calculation
    t_critical = stats.t.ppf((1 + conf_interval) / 2, df=n-1)
    margin_of_error_mean = t_critical * error_std
    lower_bound_mean = mean - margin_of_error_mean
    upper_bound_mean = mean + margin_of_error_mean
    
    # Quantify data points outside the confidence interval
    outside_conf_interval_mean = np.sum((sample < lower_bound_mean) | (sample > upper_bound_mean))
    proportion_outside_mean = outside_conf_interval_mean / n * 100
    
    print(f"Mean of the data: {mean:.2f} km²")
    print(f"Standard deviation: {std_dev:.2f} km²")
    print(f"Standard error of the mean: {error_std:.2f} km²")
    print(f"{int(conf_interval*100)}% Confidence Interval for Mean: [{lower_bound_mean:.2f}, {upper_bound_mean:.2f}] km²")
    print(f"Number of data points outside the CI for Mean: {outside_conf_interval_mean}")
    print(f"Proportion of data points outside the CI for Mean: {proportion_outside_mean:.2f}%")
    
    # Plotting the results for Mean
    plt.figure(figsize=(12, 6))
    indices = np.arange(1, n + 1)
    plt.plot(indices, sample, 'o', label='Sample Data', color='blue')
    plt.axhline(mean, color='red', linestyle='--', label='Mean')
    plt.fill_between(indices, lower_bound_mean, upper_bound_mean, color='gray', alpha=0.2, label=f'{int(conf_interval*100)}% CI for Mean')
    plt.xlabel('Sample Index')
    plt.ylabel('Value (km²)')
    plt.title('Sample Data with Mean and CI for Mean')
    plt.legend()
    plt.ylim(min(lower_bound_mean, np.min(sample)) - 0.05, max(upper_bound_mean, np.max(sample)) + 0.05)
    plt.grid(True)
    plt.show()
    
else:
    print("The data does not appear to be normally distributed. Confidence Interval for Median may be more robust.")
    
    # Calculate and plot Confidence Interval for Median
    median = np.median(sample)
    lower_percentile = (1 - conf_interval) / 2 * 100
    upper_percentile = (1 + conf_interval) / 2 * 100
    lower_bound_median = np.percentile(sample, lower_percentile)
    upper_bound_median = np.percentile(sample, upper_percentile)
    
    # Quantify data points outside the confidence interval
    outside_conf_interval_median = np.sum((sample < lower_bound_median) | (sample > upper_bound_median))
    proportion_outside_median = outside_conf_interval_median / n * 100
    
    print(f"Median of the data: {median:.2f} km²")
    print(f"{int(conf_interval*100)}% Confidence Interval for Median: [{lower_bound_median:.2f}, {upper_bound_median:.2f}] km²")
    print(f"Number of data points outside the CI for Median: {outside_conf_interval_median}")
    print(f"Proportion of data points outside the CI for Median: {proportion_outside_median:.2f}%")
    
    # Plotting the results for Median
    plt.figure(figsize=(12, 6))
    indices = np.arange(1, n + 1)
    plt.plot(indices, sample, 'o', label='Sample Data', color='blue')
    plt.axhline(median, color='green', linestyle='--', label='Median')
    plt.fill_between(indices, lower_bound_median, upper_bound_median, color='gray', alpha=0.2, label=f'{int(conf_interval*100)}% CI for Median')
    plt.xlabel('Sample Index')
    plt.ylabel('Value (km²)')
    plt.title('Sample Data with Median and CI for Median')
    plt.legend()
    plt.ylim(min(lower_bound_median, np.min(sample)) - 0.05, max(upper_bound_median, np.max(sample)) + 0.05)
    plt.grid(True)
    plt.show()
