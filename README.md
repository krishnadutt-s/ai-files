# ai-files
workshop notebooks

# 📊 Probability Basics

Probability is the measure of the likelihood that an event will occur.  
It ranges from **0** (impossible) to **1** (certain).

---

## 1️⃣ Key Terms

- **Experiment**: A process that leads to an outcome (e.g., rolling a die).
- **Sample Space (S)**: The set of all possible outcomes.
  - Example: For a coin toss, `S = {Heads, Tails}`
- **Event (E)**: A subset of the sample space.
  - Example: Getting a head in a coin toss.

---

## 2️⃣ Probability Formula

For equally likely outcomes:

\[
P(E) = \frac{\text{Number of favorable outcomes}}{\text{Total number of outcomes}}
\]

Example: Probability of rolling a 4 on a fair die:

\[
P(4) = \frac{1}{6}
\]

---

## 3️⃣ Types of Probability

### a) **Theoretical Probability**
Based on reasoning and known outcomes.
> Example: Probability of getting heads in a fair coin toss = `0.5`

### b) **Experimental Probability**
Based on actual experiments or trials.
\[
P(E) = \frac{\text{Number of times E occurs}}{\text{Total trials}}
\]

### c) **Conditional Probability**
Probability of event **A** given event **B** has occurred:
\[
P(A|B) = \frac{P(A \cap B)}{P(B)}
\]

---

## 4️⃣ Rules of Probability

1. **Complement Rule**:
   \[
   P(\text{not } E) = 1 - P(E)
   \]

2. **Addition Rule** (Mutually Exclusive Events):
   \[
   P(A \cup B) = P(A) + P(B)
   \]

3. **Multiplication Rule** (Independent Events):
   \[
   P(A \cap B) = P(A) \times P(B)
   \]

---

## 5️⃣ Common Distributions

- **Uniform Distribution**: All outcomes equally likely.
- **Binomial Distribution**: Number of successes in fixed trials.
- **Normal Distribution**: Bell-shaped curve, common in nature.
- **Poisson Distribution**: Number of events in fixed interval.

---

## 6️⃣ Example in R

```r
# Probability of getting heads in coin toss simulation
set.seed(123)
trials <- 1000
results <- sample(c("Heads", "Tails"), trials, replace = TRUE)
prob_heads <- sum(results == "Heads") / trials
print(prob_heads)
