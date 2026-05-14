# Fitting-Poisson-Distribution
Aim:
To fit Poisson distribution for the arrival of objects per minute from the feeder.
Software required: Python and Visual component tool
Theory:
The Poisson distribution is the discrete probability distribution of the number of events occurring in a given time period, given the average number of times the event occurs over that time period.
If 𝜆 is mean, then the probability mass function of Poisson distribution is :
P(X=x)=e^(-λ)   λ^x/x!  ,x=0,1,2,…

Conditions for Poisson distribution:
	An event can occur any number of times during a time period.
	Events occur independently.
	The rate of occurrence is constant.
	The probability of an even occurring is proportional to the length of the time period.
Procedure:
	Compute mean= ∑𝑓𝑥 = ∑𝑓.
𝑁
	Calculate the expected frequencies from the probability mass function 
P(X=x)=e^(-λ)   λ^x/x!  ,x=0,1,2,…

	Calculate the expected frequencies
𝑁 × 𝑃(𝑋 = 𝑥); 𝑥 = 0,1,2, ⋯

	Calculate χ^2=∑▒(O-E)^2/E, where O and E are expected and observed frequencies.

	Test 𝜒2 at 1% level of significance and write the conclusion.
  #Program
  ```
# Chi-Square Test for Poisson Distribution

import math

# -----------------------------
# INPUT OBSERVED FREQUENCIES
# -----------------------------
# x values
x = [0, 1, 2, 3, 4]

# observed frequencies corresponding to x
f = [12, 18, 10, 7, 3]

# -----------------------------
# STEP 1 : Calculate Mean
# -----------------------------
N = sum(f)

fx = [x[i] * f[i] for i in range(len(x))]
sum_fx = sum(fx)

mean = sum_fx / N

print("Total Frequency (N) =", N)
print("Sum of fx =", sum_fx)
print("Mean =", mean)

# λ for Poisson distribution
lam = mean

# -----------------------------
# STEP 2 : Calculate Probabilities
# P(X=x)=e^(-λ) * λ^x / x!
# -----------------------------
probabilities = []

for xi in x:
    p = math.exp(-lam) * (lam ** xi) / math.factorial(xi)
    probabilities.append(p)

print("\nPoisson Probabilities:")
for i in range(len(x)):
    print(f"P(X={x[i]}) = {probabilities[i]:.5f}")

# -----------------------------
# STEP 3 : Expected Frequencies
# E = N * P(X=x)
# -----------------------------
expected = [N * p for p in probabilities]

print("\nExpected Frequencies:")
for i in range(len(x)):
    print(f"E({x[i]}) = {expected[i]:.4f}")

# -----------------------------
# STEP 4 : Chi-Square Calculation
# χ² = Σ (O-E)^2 / E
# -----------------------------
chi_square = 0

print("\nChi-Square Table:")
print("x\tO\tE\t(O-E)^2/E")

for i in range(len(x)):
    O = f[i]
    E = expected[i]

    chi = ((O - E) ** 2) / E
    chi_square += chi

    print(f"{x[i]}\t{O}\t{E:.4f}\t{chi:.4f}")

print("\nCalculated Chi-Square =", chi_square)

# -----------------------------
# STEP 5 : Hypothesis Testing
# -----------------------------
# Example:
# degrees of freedom = number of classes - parameters estimated - 1
df = len(x) - 1 - 1

# χ² critical value at 1% significance level
# For df = 3, critical value ≈ 11.345

critical_value = 11.345

print("\nDegrees of Freedom =", df)
print("Critical Value at 1% level =", critical_value)

if chi_square < critical_value:
    print("\nConclusion:")
    print("Accept H0")
    print("Poisson distribution fits the data.")
else:
    print("\nConclusion:")
    print("Reject H0")
    print("Poisson distribution does not fit the data.")
    ```
 ```
#Output:
<img width="281" height="102" alt="image" src="https://github.com/user-attachments/assets/42bd7047-c22b-4fab-b485-1f4bb16c2c03" />
<img width="313" height="158" alt="image" src="https://github.com/user-attachments/assets/96cff830-a894-4702-95c7-903af6a43ed1" />
<img width="317" height="172" alt="image" src="https://github.com/user-attachments/assets/f71704ec-13d3-48bf-811c-13fa47d4118f" />
<img width="380" height="141" alt="image" src="https://github.com/user-attachments/assets/4b72c7fd-1773-45f4-b551-cdcc94587509" />
#Result:
thus the code run successfully  and got the output


