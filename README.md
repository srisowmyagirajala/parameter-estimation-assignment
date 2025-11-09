# parameter-estimation-assignment
unknown-variable-estimation



---

## 🔹 Objective
Estimate the unknown parameters **θ**, **M**, and **X** in the given parametric equations using **L1 distance minimization** between observed and predicted data points.

---

## 🔹 Given Model Equations


x(t) = t*cos(theta) - exp(M*abs(t))*sin(0.3*t)*sin(theta) + X

y(t) = 42 + t*sin(theta) + exp(M*abs(t))*sin(0.3*t)*cos(theta)

Where:
- \( t \) — parameter uniformly sampled between 6 and 60  
- \( \theta \) — rotation angle (degrees or radians)  
- \( M \) — exponential scaling parameter  
- \( X \) — horizontal offset  

---

## 🔹 Approach & Steps

1. **Data Loading:**  
   Loaded `xy_data.csv` with 1500 points.

2. **Model Definition:**  
   Created `model_xy()` to generate predicted \(x, y\) values for given \(t, \theta, M, X\).

3. **Loss Function (L1):**

   L1 = Σ ( |x_i - x_pred,i| + |y_i - y_pred,i| )

   Used because it is robust to outliers.

4. **Initialization (Grid Search):**  
   Coarse search over:
   - θ ∈ [1°, 49°]  
   - M ∈ [-0.045, 0.045]  
   - X estimated as mean offset  

5. **Optimization:**  
   Refined using **L-BFGS-B** algorithm (`scipy.optimize.minimize`) under parameter bounds.

6. **Sorting:**  
   Performed fitting after sorting data by **x** (for consistent parameter mapping).

7. **Result Evaluation:**  
   Computed Total and Average L1 losses.

---

## 🔹 Results

| Parameter | Symbol | Value |
|------------|----------|--------|
| Angle | \( \theta \) | 30.0436° |
| Exponential Rate | \( M \) | 0.029991 |
| X-Offset | \( X \) | 55.0155 |

**Total L1 = 453.4369**  
**Average L1 = 0.3023**

---

## 🔹 Final Fitted Model

In **LaTeX format:**

\[
\left(t\cos(0.5244) - e^{0.029991|t|}\sin(0.3t)\sin(0.5244) + 55.0155,\;
42 + t\sin(0.5244) + e^{0.029991|t|}\sin(0.3t)\cos(0.5244)\right)
\]

*(0.5244 rad ≈ 30.0436°)*

---

## 🔹 Desmos Format (for submission)
Copy this directly into [Desmos Graphing Calculator](https://www.desmos.com/calculator/ekngv8vkax):

