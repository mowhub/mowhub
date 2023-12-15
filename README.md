# Define the Korsmeyer-Peppas model equation
def korsmeyer_peppas(t, k, n):
    return k * (t ** n)

# Sample dissolution profile data (replace with your actual data)
time = np.array([1, 2, 3, 4.5, 6, 8])
release_percentage = np.array([40.43, 72.8, 87.4, 109.5, 114.9, 89.87])

# Fit the model to the data
params, covariance = curve_fit(korsmeyer_peppas, time, release_percentage)

# Extract fitted parameters
k_fit, n_fit = params

# Generate predicted values using the fitted model
predicted_values = korsmeyer_peppas(time, k_fit, n_fit)

# Plot the experimental data and the fitted curve
plt.scatter(time, release_percentage, label='Experimental Data')
plt.plot(time, predicted_values, label=f'Fitted Curve (k={k_fit:.2f}, n={n_fit:.2f})')
plt.xlabel('Time')
plt.ylabel('Release Percentage')
plt.legend()
plt.show()
