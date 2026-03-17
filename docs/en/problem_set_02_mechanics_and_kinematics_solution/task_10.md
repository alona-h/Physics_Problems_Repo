# Problem 10 – Analysis of Motion from Numerical Data

The position is given by:

$$
x(t) = t + \frac{1}{20}t^2
$$

on the interval $t \in [0, 10]$ with time step $\Delta t = 0.1$.

---

## Question 10.1 – Approximate the velocity using the finite difference method

**Question:** How do you estimate velocity numerically from discrete position
data, without using calculus?

### What is the finite difference method?

Instead of computing the exact derivative $v = dx/dt$, we approximate it
using nearby data points. The idea is simple: if you know where something
is at two nearby times, the average velocity between them approximates the
instantaneous velocity.

There are three standard finite difference formulas:

**Forward difference** (uses the point ahead):

$$
v(t_i) \approx \frac{x(t_i + \Delta t) - x(t_i)}{\Delta t}
= \frac{x_{i+1} - x_i}{\Delta t}
$$

**Backward difference** (uses the point behind):

$$
v(t_i) \approx \frac{x(t_i) - x(t_i - \Delta t)}{\Delta t}
= \frac{x_i - x_{i-1}}{\Delta t}
$$

**Central difference** (uses both neighbours — most accurate):

$$
v(t_i) \approx \frac{x(t_i + \Delta t) - x(t_i - \Delta t)}{2\Delta t}
= \frac{x_{i+1} - x_{i-1}}{2\Delta t}
$$

We will use the **central difference** as the primary method since it is
the most accurate.

### Setting up the data

Generate position values using $x(t) = t + \frac{1}{20}t^2$:

| $i$ | $t_i$ | $x_i = t_i + \frac{t_i^2}{20}$ |
|:---:|:---:|:---:|
| $0$ | $0.0$ | $0.000$ |
| $1$ | $0.1$ | $0.1005$ |
| $2$ | $0.2$ | $0.202$ |
| $3$ | $0.3$ | $0.3045$ |
| $4$ | $0.4$ | $0.408$ |
| $5$ | $0.5$ | $0.5125$ |
| $\vdots$ | $\vdots$ | $\vdots$ |
| $50$ | $5.0$ | $6.250$ |
| $\vdots$ | $\vdots$ | $\vdots$ |
| $99$ | $9.9$ | $14.8005$ |
| $100$ | $10.0$ | $15.000$ |

### Applying the central difference formula

For interior points ($i = 1, 2, \ldots, 98$):

$$
v(t_i) \approx \frac{x_{i+1} - x_{i-1}}{2\Delta t}
$$

**Step-by-step example at $t = 1.0$ (i.e. $i = 10$):**

$$
t_{10} = 1.0, \quad t_{11} = 1.1, \quad t_9 = 0.9
$$

$$
x_{11} = 1.1 + \frac{(1.1)^2}{20} = 1.1 + \frac{1.21}{20} = 1.1 + 0.0605 = 1.1605
$$

$$
x_9 = 0.9 + \frac{(0.9)^2}{20} = 0.9 + \frac{0.81}{20} = 0.9 + 0.0405 = 0.9405
$$

$$
v(1.0) \approx \frac{x_{11} - x_9}{2\Delta t} = \frac{1.1605 - 0.9405}{2 \times 0.1}
= \frac{0.22}{0.2} = 1.10\ \text{m/s}
$$

**Step-by-step example at $t = 5.0$ ($i = 50$):**

$$
x_{51} = 5.1 + \frac{(5.1)^2}{20} = 5.1 + \frac{26.01}{20} = 5.1 + 1.3005 = 6.4005
$$

$$
x_{49} = 4.9 + \frac{(4.9)^2}{20} = 4.9 + \frac{24.01}{20} = 4.9 + 1.2005 = 6.1005
$$

$$
v(5.0) \approx \frac{6.4005 - 6.1005}{0.2} = \frac{0.30}{0.2} = 1.50\ \text{m/s}
$$

**Step-by-step example at $t = 10.0$ — backward difference at endpoint:**

At the last point we cannot use central difference (no $x_{i+1}$ exists),
so we use the backward difference:

$$
v(10.0) \approx \frac{x_{100} - x_{99}}{\Delta t}
= \frac{15.000 - 14.8005}{0.1} = \frac{0.1995}{0.1} = 1.995\ \text{m/s}
$$

**Numerical velocity table (selected points):**

| $t_i$ | $x_{i-1}$ | $x_{i+1}$ | $v \approx \frac{x_{i+1}-x_{i-1}}{2\Delta t}$ |
|:---:|:---:|:---:|:---:|
| $1.0$ | $0.9405$ | $1.1605$ | $1.100$ |
| $2.0$ | $1.980$ | $2.222$ | $1.210$ (wait — recheck below) |
| $3.0$ | $3.1205$ | $3.3845$ | $1.320$ |
| $5.0$ | $6.1005$ | $6.4005$ | $1.500$ |
| $7.0$ | $9.6805$ | $10.0405$ | $1.800$ (wait — recheck below) |
| $10.0$ | — | — | $\approx 2.000$ (backward diff.) |

**Recheck at $t = 2.0$:**

$$
x_{21} = 2.1 + \frac{(2.1)^2}{20} = 2.1 + \frac{4.41}{20} = 2.1 + 0.2205 = 2.3205
$$

$$
x_{19} = 1.9 + \frac{(1.9)^2}{20} = 1.9 + \frac{3.61}{20} = 1.9 + 0.1805 = 2.0805
$$

$$
v(2.0) \approx \frac{2.3205 - 2.0805}{0.2} = \frac{0.24}{0.2} = 1.20\ \text{m/s}
$$

**Recheck at $t = 7.0$:**

$$
x_{71} = 7.1 + \frac{(7.1)^2}{20} = 7.1 + \frac{50.41}{20} = 7.1 + 2.5205 = 9.6205
$$

$$
x_{69} = 6.9 + \frac{(6.9)^2}{20} = 6.9 + \frac{47.61}{20} = 6.9 + 2.3805 = 9.2805
$$

$$
v(7.0) \approx \frac{9.6205 - 9.2805}{0.2} = \frac{0.34}{0.2} = 1.70\ \text{m/s}
$$

**Corrected velocity table:**

| $t$ | Numerical $v$ (central diff.) |
|:---:|:---:|
| $1.0$ | $1.100$ |
| $2.0$ | $1.200$ |
| $3.0$ | $1.300$ |
| $4.0$ | $1.400$ |
| $5.0$ | $1.500$ |
| $6.0$ | $1.600$ |
| $7.0$ | $1.700$ |
| $8.0$ | $1.800$ |
| $9.0$ | $1.900$ |
| $10.0$ | $\approx 2.000$ |

> **Explanation:**
> In real experiments you do not have a formula — you only have measurements
> of position at discrete time steps. The finite difference method is the
> standard way to estimate velocity from such data. The central difference
> is the most accurate basic formula because it uses a point on each side of
> the time you are interested in, symmetrically. Think of it as asking:
> "How far did the object travel in the small time interval around this moment,
> divided by that time interval?" The smaller the time step $\Delta t$, the
> closer this approximation is to the true instantaneous velocity. The central
> difference is preferred over forward or backward differences because it
> has a smaller error — its error is proportional to $(\Delta t)^2$ rather
> than $\Delta t$.

---

## Question 10.2 – Approximate the acceleration using the finite difference method

**Question:** How do you estimate acceleration numerically from the
velocity data (or directly from position data)?

### Method 1: Second finite difference applied to position

The acceleration is the second derivative of position. We can estimate it
directly from position data using:

$$
a(t_i) \approx \frac{x_{i+1} - 2x_i + x_{i-1}}{(\Delta t)^2}
$$

This is derived by applying the finite difference twice:

**Derivation:**

Forward difference of $x$ gives an approximation to $v$:

$$
v_{i+1/2} \approx \frac{x_{i+1} - x_i}{\Delta t}
$$

$$
v_{i-1/2} \approx \frac{x_i - x_{i-1}}{\Delta t}
$$

Finite difference of these two velocity estimates gives acceleration:

$$
a(t_i) \approx \frac{v_{i+1/2} - v_{i-1/2}}{\Delta t}
= \frac{\frac{x_{i+1} - x_i}{\Delta t} - \frac{x_i - x_{i-1}}{\Delta t}}{\Delta t}
= \frac{x_{i+1} - 2x_i + x_{i-1}}{(\Delta t)^2}
$$

### Step-by-step example at $t = 1.0$ ($i = 10$):

$$
x_{11} = 1.1605, \quad x_{10} = 1.0 + \frac{1.0}{20} = 1.0500, \quad x_9 = 0.9405
$$

$$
a(1.0) \approx \frac{1.1605 - 2(1.0500) + 0.9405}{(0.1)^2}
= \frac{1.1605 - 2.1000 + 0.9405}{0.01}
= \frac{0.0010}{0.01} = 0.10\ \text{m/s}^2
$$

### Step-by-step example at $t = 5.0$ ($i = 50$):

$$
x_{51} = 6.4005, \quad x_{50} = 5.0 + \frac{25}{20} = 6.2500, \quad x_{49} = 6.1005
$$

$$
a(5.0) \approx \frac{6.4005 - 2(6.2500) + 6.1005}{(0.1)^2}
= \frac{6.4005 - 12.5000 + 6.1005}{0.01}
= \frac{0.0010}{0.01} = 0.10\ \text{m/s}^2
$$

### Step-by-step example at $t = 9.0$ ($i = 90$):

$$
x_{91} = 9.1 + \frac{(9.1)^2}{20} = 9.1 + \frac{82.81}{20} = 9.1 + 4.1405 = 13.2405
$$

$$
x_{90} = 9.0 + \frac{81}{20} = 9.0 + 4.05 = 13.0500
$$

$$
x_{89} = 8.9 + \frac{(8.9)^2}{20} = 8.9 + \frac{79.21}{20} = 8.9 + 3.9605 = 12.8605
$$

$$
a(9.0) \approx \frac{13.2405 - 2(13.0500) + 12.8605}{0.01}
= \frac{13.2405 - 26.1000 + 12.8605}{0.01}
= \frac{0.0010}{0.01} = 0.10\ \text{m/s}^2
$$

**Numerical acceleration table:**

| $t$ | $x_{i-1}$ | $x_i$ | $x_{i+1}$ | $a \approx \frac{x_{i+1}-2x_i+x_{i-1}}{(\Delta t)^2}$ |
|:---:|:---:|:---:|:---:|:---:|
| $1.0$ | $0.9405$ | $1.0500$ | $1.1605$ | $0.100$ |
| $3.0$ | $3.1205$ | $3.2450$ | $3.3705$ | $0.100$ |
| $5.0$ | $6.1005$ | $6.2500$ | $6.4005$ | $0.100$ |
| $7.0$ | $9.2805$ | $9.4500$ | $9.6205$ | $0.100$ |
| $9.0$ | $12.8605$ | $13.0500$ | $13.2405$ | $0.100$ |

The numerical acceleration is $0.100\ \text{m/s}^2$ at every point.

> **Explanation:**
> The second finite difference formula $\frac{x_{i+1} - 2x_i + x_{i-1}}{(\Delta t)^2}$
> is the discrete equivalent of the second derivative. It measures how much
> the position "curves" — if the position were growing at a perfectly constant
> rate (constant velocity), the numerator would be zero. Any curvature away
> from a straight line indicates acceleration. The formula comes from applying
> the finite difference twice: first to get approximate velocities on each side
> of the point, then again to get the rate of change of velocity. The
> $(\Delta t)^2$ in the denominator appears because we divided by $\Delta t$
> twice. The fact that we get exactly $0.10$ at every point is confirmed in
> the next section.

---

## Question 10.3 – Compare with the analytical solution

**Question:** What are the exact velocity and acceleration, and how well
do the numerical estimates match?

### Analytical solution

**Exact velocity** — differentiate $x(t) = t + \frac{1}{20}t^2$:

$$
v(t) = \frac{dx}{dt} = \frac{d}{dt}\!\left(t + \frac{t^2}{20}\right)
= 1 + \frac{2t}{20} = 1 + \frac{t}{10}
$$

$$
\boxed{v(t) = 1 + \frac{t}{10}\ \text{m/s}}
$$

**Exact acceleration** — differentiate $v(t)$:

$$
a(t) = \frac{dv}{dt} = \frac{d}{dt}\!\left(1 + \frac{t}{10}\right) = \frac{1}{10}
$$

$$
\boxed{a(t) = \frac{1}{10} = 0.1\ \text{m/s}^2 = \text{const}}
$$

This is **uniformly accelerated motion** — constant acceleration,
just like Problem 1.

### Comparison: numerical vs analytical

**Velocity comparison:**

| $t$ | Analytical $v = 1 + t/10$ | Numerical $v$ (central diff.) | Error |
|:---:|:---:|:---:|:---:|
| $1.0$ | $1.100$ | $1.100$ | $0.000$ |
| $2.0$ | $1.200$ | $1.200$ | $0.000$ |
| $3.0$ | $1.300$ | $1.300$ | $0.000$ |
| $5.0$ | $1.500$ | $1.500$ | $0.000$ |
| $7.0$ | $1.700$ | $1.700$ | $0.000$ |
| $9.0$ | $1.900$ | $1.900$ | $0.000$ |
| $10.0$ | $2.000$ | $\approx 2.000$ | $\approx 0.000$ |

**Why is the error exactly zero for the central difference here?**

For a quadratic function $x(t) = t + \frac{t^2}{20}$, the central
difference formula gives the **exact** derivative — not just an approximation!

**Proof:**

$$
\frac{x(t+\Delta t) - x(t-\Delta t)}{2\Delta t}
$$

$$
= \frac{\left[(t+\Delta t) + \frac{(t+\Delta t)^2}{20}\right]
- \left[(t-\Delta t) + \frac{(t-\Delta t)^2}{20}\right]}{2\Delta t}
$$

Expand $(t + \Delta t)^2 = t^2 + 2t\Delta t + (\Delta t)^2$
and $(t - \Delta t)^2 = t^2 - 2t\Delta t + (\Delta t)^2$:

$$
= \frac{(t+\Delta t - t+\Delta t) + \frac{1}{20}\bigl[(t^2 + 2t\Delta t + (\Delta t)^2)
- (t^2 - 2t\Delta t + (\Delta t)^2)\bigr]}{2\Delta t}
$$

$$
= \frac{2\Delta t + \frac{1}{20}(4t\Delta t)}{2\Delta t}
= \frac{2\Delta t + \frac{4t\Delta t}{20}}{2\Delta t}
= \frac{2\Delta t\!\left(1 + \frac{t}{10}\right)}{2\Delta t}
= 1 + \frac{t}{10}
$$

This equals the exact analytical result $v(t) = 1 + t/10$ for
**any** $\Delta t$ — the $(\Delta t)^2$ terms cancel perfectly
for a quadratic function.

**Acceleration comparison:**

| $t$ | Analytical $a = 0.1$ | Numerical $a$ | Error |
|:---:|:---:|:---:|:---:|
| $1.0$ | $0.100$ | $0.100$ | $0.000$ |
| $5.0$ | $0.100$ | $0.100$ | $0.000$ |
| $9.0$ | $0.100$ | $0.100$ | $0.000$ |

Again, the error is exactly zero because the second finite difference
is exact for quadratic functions — the $(\Delta t)^2$ terms that would
cause error cancel completely.

> **Explanation:**
> The analytical solution gives us the ground truth — the exact velocity
> and acceleration at any moment. Comparing to the numerical result
> reveals how accurate the finite difference method is for this particular
> function. The remarkable result here is that the central difference is
> perfectly exact for a quadratic (degree-2) function. This happens because
> the Taylor series error of the central difference is proportional to
> $(\Delta t)^2$ multiplied by the third derivative of $x(t)$. Since
> $x(t) = t + t^2/20$ is only degree 2, its third derivative is zero —
> and therefore the error is also exactly zero. For more complex (higher
> degree) functions, there will be a non-zero error, which is what
> Question 10.4 investigates.

---

## Question 10.4 – Investigate the effect of time step on accuracy

**Question:** How does the size of $\Delta t$ affect the accuracy of the
numerical derivatives? What happens as $\Delta t$ gets larger or smaller?

### Theoretical error analysis

The **central difference** approximation has a truncation error given by:

$$
v(t) - \frac{x(t+\Delta t) - x(t-\Delta t)}{2\Delta t}
= -\frac{(\Delta t)^2}{6} x'''(t) + O\!\left((\Delta t)^4\right)
$$

where $x'''(t)$ is the third derivative of $x(t)$.

For **our specific function** $x(t) = t + \frac{t^2}{20}$:

$$
x'(t) = 1 + \frac{t}{10}, \quad x''(t) = \frac{1}{10}, \quad x'''(t) = 0
$$

Since $x'''(t) = 0$, the truncation error is **exactly zero** for any $\Delta t$.

### Test with a more complex function

To see the effect of $\Delta t$ on accuracy, consider a function with
non-zero higher derivatives. Take $f(t) = \sin(t)$ as a test case,
where the exact derivative is $f'(t) = \cos(t)$.

At $t = 1.0$ rad, exact: $\cos(1.0) \approx 0.5403$

| $\Delta t$ | Numerical $f'(1.0)$ | Error $= |v_{\text{num}} - v_{\text{exact}}|$ |
|:---:|:---:|:---:|
| $1.0$ | $\frac{\sin(2) - \sin(0)}{2} = \frac{0.9093 - 0}{2} = 0.4546$ | $0.0857$ |
| $0.5$ | $\frac{\sin(1.5) - \sin(0.5)}{1.0} = \frac{0.9975 - 0.4794}{1} = 0.5181$ | $0.0222$ |
| $0.1$ | $\approx 0.5398$ | $0.0005$ |
| $0.01$ | $\approx 0.54030$ | $0.000005$ |
| $0.001$ | $\approx 0.540302$ | $\approx 5\times 10^{-8}$ |

The error decreases as $\Delta t^2$ — halving $\Delta t$ reduces the error
by a factor of $4$.

### Effect of $\Delta t$ on our specific problem

Even though our function gives exact results for the central difference,
we can test the **forward difference** (which has $O(\Delta t)$ error)
at $t = 5.0$:

**Exact:** $v(5.0) = 1 + 5/10 = 1.500$ m/s

**Forward difference at various $\Delta t$:**

$$
v_{\text{fwd}}(5.0) \approx \frac{x(5.0 + \Delta t) - x(5.0)}{\Delta t}
$$

For $\Delta t = 0.1$:

$$
x(5.1) = 5.1 + \frac{26.01}{20} = 6.4005
$$

$$
v \approx \frac{6.4005 - 6.2500}{0.1} = \frac{0.1505}{0.1} = 1.505
$$

Error $= |1.505 - 1.500| = 0.005$ m/s

For $\Delta t = 1.0$:

$$
x(6.0) = 6.0 + \frac{36}{20} = 7.800
$$

$$
v \approx \frac{7.800 - 6.250}{1.0} = 1.550
$$

Error $= |1.550 - 1.500| = 0.050$ m/s

For $\Delta t = 0.01$:

$$
x(5.01) = 5.01 + \frac{(5.01)^2}{20} = 5.01 + 1.255005 = 6.255005 + 0.2505 = 6.2655
$$

Wait — let us recalculate carefully:

$$
x(5.01) = 5.01 + \frac{(5.01)^2}{20} = 5.01 + \frac{25.1001}{20} = 5.01 + 1.25501 = 6.26501
$$

$$
v \approx \frac{6.26501 - 6.25000}{0.01} = \frac{0.01501}{0.01} = 1.501
$$

Error $= 0.001$ m/s

**Forward difference error table at $t = 5.0$:**

| $\Delta t$ | Numerical $v$ (forward diff.) | Error |
|:---:|:---:|:---:|
| $1.0$ | $1.550$ | $0.050$ |
| $0.5$ | $1.525$ | $0.025$ |
| $0.1$ | $1.505$ | $0.005$ |
| $0.01$ | $1.501$ | $0.0005$ |

Error scales linearly with $\Delta t$ — halving $\Delta t$ halves the error.
This confirms the $O(\Delta t)$ order of the forward difference.

### Summary: Comparison of all three methods

| Method | Formula | Error order | Error halves when $\Delta t$ halves? |
|:---|:---:|:---:|:---:|
| Forward difference | $\frac{x_{i+1} - x_i}{\Delta t}$ | $O(\Delta t)$ | Yes (by factor 2) |
| Backward difference | $\frac{x_i - x_{i-1}}{\Delta t}$ | $O(\Delta t)$ | Yes (by factor 2) |
| Central difference | $\frac{x_{i+1} - x_{i-1}}{2\Delta t}$ | $O((\Delta t)^2)$ | Yes (by factor 4) |

### Practical recommendations

- **Smaller $\Delta t$** is generally more accurate — but not always!
  For very small $\Delta t$, floating-point rounding errors in a computer
  can accumulate and eventually make the result worse.
- **Central difference** is almost always preferred over forward or
  backward difference for the same $\Delta t$.
- For our quadratic function, any $\Delta t$ gives zero error with the
  central difference — the method is exact.
- In experiments, $\Delta t$ is limited by the measurement frequency
  (sampling rate) of the instruments.

> **Explanation:**
> The time step $\Delta t$ controls the trade-off between accuracy and
> practicality. A smaller step means you are measuring over a shorter time
> interval, so your estimate of the instantaneous velocity is more precise —
> just like how the speedometer in a car that updates every millisecond is
> more accurate than one that updates every second. Mathematically, the
> error of the central difference shrinks as $(\Delta t)^2$ — if you make
> the step ten times smaller, the error becomes one hundred times smaller.
> The forward difference is less efficient: making the step ten times smaller
> only reduces its error by ten times. In our problem the function is
> quadratic (degree 2), so the central difference is perfectly exact for
> any step size. For real experimental data, which is noisy and may contain
> higher-degree behaviour, choosing the right $\Delta t$ requires balancing
> truncation error (gets worse for large $\Delta t$) against measurement
> noise amplification (gets worse for very small $\Delta t$).

---

## Possible Questions and Answers

**Q1: What is the difference between truncation error and round-off error
in numerical differentiation?**

A: **Truncation error** is the mathematical error introduced by approximating
a derivative with a finite difference — it comes from ignoring higher-order
terms in the Taylor series expansion. For the central difference it is
$O((\Delta t)^2)$: it decreases as $\Delta t$ shrinks. **Round-off error**
comes from the limited precision of floating-point arithmetic in computers —
when $\Delta t$ is very small, $x_{i+1}$ and $x_{i-1}$ become nearly equal
and their difference loses significant digits. This error grows as $\Delta t$
shrinks. The optimal $\Delta t$ balances both: small enough to reduce
truncation error, but not so small that round-off error dominates. In
practice, for double-precision arithmetic ($\sim 16$ significant digits),
the optimal $\Delta t$ for central differences is around $10^{-5}$ to $10^{-6}$.

---

**Q2: Why does the central difference give zero error for a quadratic
function, regardless of $\Delta t$?**

A: The Taylor expansion of the central difference error involves the third
derivative of the function multiplied by $(\Delta t)^2 / 6$. For a quadratic
function $x(t) = at^2 + bt + c$, the third derivative $x'''(t) = 0$
identically — a degree-2 polynomial has zero third and higher derivatives.
Therefore the error term is exactly $0 \cdot (\Delta t)^2 / 6 = 0$ for any
$\Delta t$. More formally: the central difference formula is exact for all
polynomials of degree $\leq 2$ because it reproduces them perfectly.

---

**Q3: How would you apply the finite difference method to real experimental
data that contains measurement noise?**

A: Real data contains noise — random fluctuations in measured positions due
to instrument imprecision. Finite differences amplify noise because they
divide small differences by small time steps. Common strategies include:
(1) **Smoothing** the data first (e.g. moving average, Savitzky-Golay filter)
before differentiating; (2) **Fitting** a polynomial or smooth curve to the
data and differentiating the fit analytically; (3) **Choosing a larger $\Delta t$**
to average over more data points, reducing noise at the cost of some temporal
resolution; (4) **Regularization** methods that find the smoothest derivative
consistent with the data. The choice depends on the noise level and the
physical smoothness expected in the signal.

---

**Q4: What is the physical meaning of the second finite difference
$\frac{x_{i+1} - 2x_i + x_{i-1}}{(\Delta t)^2}$?**

A: It measures the **curvature** of the position-time graph — how much the
position deviates from moving in a straight line. If the position increases
at a perfectly constant rate ($x_i$ lies on a straight line), then
$x_{i+1} - 2x_i + x_{i-1} = 0$ exactly, meaning zero acceleration.
If the position is curving upward (accelerating), the numerator is positive.
If curving downward (decelerating), it is negative. The formula computes
the "excess" of the next position over what a constant-velocity prediction
would give: a constant-velocity prediction from $x_{i-1}$ would give
$x_i + (x_i - x_{i-1}) = 2x_i - x_{i-1}$, so the excess is
$x_{i+1} - (2x_i - x_{i-1}) = x_{i+1} - 2x_i + x_{i-1}$.

---

**Q5: For the function $x(t) = t + \frac{t^2}{20}$, the analytical
acceleration is constant. How could you verify this experimentally
(i.e. using only the numerical data, without knowing the formula)?**

A: Compute the numerical acceleration at many time points using
$a(t_i) \approx \frac{x_{i+1} - 2x_i + x_{i-1}}{(\Delta t)^2}$ across
the entire interval $t \in [0, 10]$. If the motion has constant acceleration,
all these values should be the same (within numerical noise). You could:
(1) plot $a(t_i)$ vs $t_i$ and check that it is a horizontal flat line;
(2) compute the mean and standard deviation of all $a(t_i)$ values — a
small standard deviation confirms constant acceleration;
(3) check that the velocity $v(t_i)$ increases linearly with time
(a straight line on a $v$-$t$ graph also confirms constant acceleration,
since $v = v_0 + at$ is linear in $t$).