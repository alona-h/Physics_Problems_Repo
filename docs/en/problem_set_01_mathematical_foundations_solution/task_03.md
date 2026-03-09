# Problem Set 1 – Problem 3: Integration of Motion

---

## Overview

This problem works in the **reverse direction** from Problem 2. Instead of differentiating position to get velocity and acceleration, we now *integrate* to recover position from velocity, or velocity from acceleration. This is the mathematical foundation of how physicists reconstruct the full motion of an object when only partial information (like a sensor reading acceleration) is available.

> **Key idea:** Differentiation and integration are inverse operations.
> - Position → (differentiate) → Velocity → (differentiate) → Acceleration
> - Acceleration → (integrate) → Velocity → (integrate) → Position

---

## Part A – Given velocity, find position and acceleration

**Given:**
$$\vec{v}(t) = (2t,\ 3,\ -e^{-t}), \qquad \vec{r}(0) = (0,\ 1,\ 2)$$

---

### A.1 – Position vector $\vec{r}(t)$

The formula is:
$$\vec{r}(t) = \vec{r}(0) + \int_0^t \vec{v}(\tau)\, d\tau$$

> **Explanation of the formula:** This says: start at your initial position $\vec{r}(0)$, then add up all the tiny displacements $\vec{v}(\tau)\,d\tau$ accumulated from time $0$ to time $t$. The variable $\tau$ (tau) is just a "dummy" integration variable — it plays the role of time inside the integral so we don't confuse it with the upper limit $t$.

We integrate each component of $\vec{v}(\tau) = (2\tau, 3, -e^{-\tau})$ separately:

**$x$-component:**
$$\int_0^t 2\tau\, d\tau = \left[\tau^2\right]_0^t = t^2 - 0 = t^2$$

**$y$-component:**
$$\int_0^t 3\, d\tau = \left[3\tau\right]_0^t = 3t - 0 = 3t$$

**$z$-component:**
$$\int_0^t -e^{-\tau}\, d\tau = \left[e^{-\tau}\right]_0^t = e^{-t} - e^{0} = e^{-t} - 1$$

> **Note on the $z$-integral:** Recall that $\int e^{-\tau}\,d\tau = -e^{-\tau} + C$, so $\int -e^{-\tau}\,d\tau = e^{-\tau} + C$. Evaluating from $0$ to $t$: $e^{-t} - e^{0} = e^{-t} - 1$.

**Now add the initial condition $\vec{r}(0) = (0, 1, 2)$:**

$$\vec{r}(t) = (0,\ 1,\ 2) + (t^2,\ 3t,\ e^{-t} - 1)$$

$$= (0 + t^2,\ 1 + 3t,\ 2 + e^{-t} - 1)$$

$$\boxed{\vec{r}(t) = \bigl(t^2,\ 1 + 3t,\ 1 + e^{-t}\bigr)}$$

**Verification at $t = 0$:**
$$\vec{r}(0) = (0^2,\ 1 + 0,\ 1 + e^0) = (0,\ 1,\ 2) \checkmark$$

> **Explanation:** The initial condition $\vec{r}(0)$ acts as a "starting point" — the constant of integration that integration alone cannot determine. Without knowing where the object *started*, we could only know how it moved relative to its starting position, not where it actually is in space. Adding $\vec{r}(0)$ pins down the absolute position.

---

### A.2 – Acceleration $\vec{a}(t)$

Acceleration is the derivative of velocity:
$$\vec{a}(t) = \frac{d\vec{v}}{dt}$$

Differentiating $\vec{v}(t) = (2t,\ 3,\ -e^{-t})$ component by component:

**$x$-component:**
$$\frac{d}{dt}(2t) = 2$$

**$y$-component:**
$$\frac{d}{dt}(3) = 0$$

**$z$-component:**
$$\frac{d}{dt}(-e^{-t}) = -(-1)e^{-t} = e^{-t}$$

> **Note on the $z$-derivative:** Using the chain rule, $\frac{d}{dt}(e^{-t}) = e^{-t} \cdot (-1) = -e^{-t}$. So $\frac{d}{dt}(-e^{-t}) = -(-e^{-t}) = e^{-t}$.

$$\boxed{\vec{a}(t) = (2,\ 0,\ e^{-t})}$$

> **Explanation:** The $x$-acceleration is constant at $2$ — like uniform horizontal acceleration. The $y$-acceleration is $0$ — the object moves at a steady $3$ units/time in the $y$-direction, never speeding up or slowing down in that direction. The $z$-acceleration is $e^{-t}$, which starts at $1$ when $t=0$ and decays toward $0$ as $t \to \infty$ — the object's vertical acceleration fades away exponentially over time.

---

## Part B – Given acceleration, find velocity and position

**Given:**
$$\vec{a}(t) = (4,\ -\sin t,\ 0), \qquad \vec{v}(0) = (1,\ 0,\ 2), \qquad \vec{r}(0) = (0,\ 0,\ 0)$$

---

### B.1 – Velocity $\vec{v}(t)$

The formula is:
$$\vec{v}(t) = \vec{v}(0) + \int_0^t \vec{a}(\tau)\, d\tau$$

We integrate each component of $\vec{a}(\tau) = (4,\ -\sin\tau,\ 0)$:

**$x$-component:**
$$\int_0^t 4\, d\tau = \left[4\tau\right]_0^t = 4t$$

**$y$-component:**
$$\int_0^t -\sin\tau\, d\tau = \left[\cos\tau\right]_0^t = \cos t - \cos 0 = \cos t - 1$$

> **Note:** Recall $\int \sin\tau\, d\tau = -\cos\tau + C$, so $\int -\sin\tau\, d\tau = \cos\tau + C$. Evaluating from $0$ to $t$: $\cos t - \cos 0 = \cos t - 1$.

**$z$-component:**
$$\int_0^t 0\, d\tau = 0$$

**Adding the initial condition $\vec{v}(0) = (1,\ 0,\ 2)$:**

$$\vec{v}(t) = (1,\ 0,\ 2) + (4t,\ \cos t - 1,\ 0)$$

$$= (1 + 4t,\ \cos t - 1,\ 2)$$

$$\boxed{\vec{v}(t) = (1 + 4t,\ \cos t - 1,\ 2)}$$

**Verification at $t = 0$:**
$$\vec{v}(0) = (1 + 0,\ \cos 0 - 1,\ 2) = (1,\ 1 - 1,\ 2) = (1,\ 0,\ 2) \checkmark$$

> **Explanation:** The $x$-velocity grows linearly in time — this is classic constant-acceleration motion (like free fall). The $y$-velocity oscillates as $\cos t - 1$: it starts at $0$, becomes negative (the object moves in the $-y$ direction), then returns toward $0$, oscillating back and forth. The $z$-velocity stays at a constant $2$ forever, because there is no $z$-acceleration to change it.

---

### B.2 – Position $\vec{r}(t)$

The formula is:
$$\vec{r}(t) = \vec{r}(0) + \int_0^t \vec{v}(\tau)\, d\tau$$

We integrate each component of $\vec{v}(\tau) = (1 + 4\tau,\ \cos\tau - 1,\ 2)$:

**$x$-component:**
$$\int_0^t (1 + 4\tau)\, d\tau = \left[\tau + 2\tau^2\right]_0^t = t + 2t^2$$

> **Step by step:** $\int 1\, d\tau = \tau$ and $\int 4\tau\, d\tau = 4 \cdot \frac{\tau^2}{2} = 2\tau^2$. Combined and evaluated from $0$ to $t$: $t + 2t^2 - 0 = t + 2t^2$.

**$y$-component:**
$$\int_0^t (\cos\tau - 1)\, d\tau = \left[\sin\tau - \tau\right]_0^t = (\sin t - t) - (0 - 0) = \sin t - t$$

> **Step by step:** $\int \cos\tau\, d\tau = \sin\tau$ and $\int -1\, d\tau = -\tau$. Evaluated from $0$ to $t$: $(\sin t - t) - (\sin 0 - 0) = \sin t - t$.

**$z$-component:**
$$\int_0^t 2\, d\tau = \left[2\tau\right]_0^t = 2t$$

**Adding the initial condition $\vec{r}(0) = (0,\ 0,\ 0)$:**

$$\vec{r}(t) = (0,\ 0,\ 0) + (t + 2t^2,\ \sin t - t,\ 2t)$$

$$\boxed{\vec{r}(t) = \bigl(t + 2t^2,\ \sin t - t,\ 2t\bigr)}$$

**Verification at $t = 0$:**
$$\vec{r}(0) = (0 + 0,\ \sin 0 - 0,\ 0) = (0,\ 0,\ 0) \checkmark$$

> **Explanation:** Each component of the position tells a different story about the motion. The $x$-position $t + 2t^2$ grows faster and faster (quadratic growth from constant acceleration). The $y$-position $\sin t - t$ is interesting: $\sin t$ oscillates between $-1$ and $+1$, but $-t$ drifts continuously in the negative direction — so the object oscillates left and right while drifting overall in the $-y$ direction. The $z$-position $2t$ is simple linear motion: constant speed $2$ in the $z$-direction.

---

## Summary Table

### Part A

| Quantity | Result |
|---|---|
| $\vec{v}(t)$ | $(2t,\ 3,\ -e^{-t})$ *(given)* |
| $\vec{r}(t)$ | $(t^2,\ 1+3t,\ 1+e^{-t})$ |
| $\vec{a}(t)$ | $(2,\ 0,\ e^{-t})$ |

### Part B

| Quantity | Result |
|---|---|
| $\vec{a}(t)$ | $(4,\ -\sin t,\ 0)$ *(given)* |
| $\vec{v}(t)$ | $(1+4t,\ \cos t - 1,\ 2)$ |
| $\vec{r}(t)$ | $(t + 2t^2,\ \sin t - t,\ 2t)$ |

---

## 5 Possible Questions & Answers

---

**Q1: Why do we need initial conditions $\vec{r}(0)$ and $\vec{v}(0)$? What happens if they are not given?**

**A:** When we integrate, we always produce an arbitrary constant of integration — integration is only defined up to a constant. Without initial conditions, we would only know the *shape* of the motion (how position changes relative to where we started) but not the *absolute* starting point or speed. For example, integrating $\vec{v}(t) = (2t, 3, -e^{-t})$ without an initial condition gives $\vec{r}(t) = (t^2 + C_1,\ 3t + C_2,\ 1 + e^{-t} + C_3)$ — three unknown constants. The initial condition $\vec{r}(0) = (0, 1, 2)$ pins down all three constants uniquely. In physics, this reflects the fact that Newton's second law ($\vec{F} = m\vec{a}$) requires both initial position *and* initial velocity to fully determine the future motion.

---

**Q2: In Part A, how do you verify that your answer for $\vec{r}(t)$ is correct?**

**A:** There are two checks. First, substitute $t = 0$ and confirm you recover the initial condition: $\vec{r}(0) = (0, 1, 2)$. Second, differentiate your answer and confirm you recover the original velocity: $\frac{d}{dt}(t^2, 1+3t, 1+e^{-t}) = (2t, 3, -e^{-t}) = \vec{v}(t)$. Both checks pass, confirming the result. This double-check habit is very important — it catches sign errors and forgotten constants.

---

**Q3: In Part B, why does the $y$-position drift in the negative direction even though the acceleration is $-\sin t$, which oscillates symmetrically?**

**A:** The key is to look at the *velocity*, not just the acceleration. The $y$-velocity is $v_y(t) = \cos t - 1$. Since $\cos t \leq 1$ for all $t$, we have $v_y(t) = \cos t - 1 \leq 0$ always — the $y$-velocity is *never positive*. The object moves in the $-y$ direction at all times (or momentarily stops at $t = 0, 2\pi, 4\pi, \ldots$), so it continually drifts negatively. The $-t$ term in $\vec{r}_y = \sin t - t$ reflects this cumulative drift. Even though the oscillation in $\sin t$ is symmetric, the initial condition $v_y(0) = 0$ combined with the always-negative velocity ensures only negative displacement.

---

**Q4: What is the difference between using definite integrals (from $0$ to $t$) versus indefinite integrals (with $+C$) to solve these problems?**

**A:** Both approaches give the same result but via different routes. With **definite integrals**, you write $\vec{r}(t) = \vec{r}(0) + \int_0^t \vec{v}(\tau)\,d\tau$ — the initial condition is built directly into the formula, and the dummy variable $\tau$ avoids confusion with the upper limit $t$. With **indefinite integrals**, you write $\vec{r}(t) = \int \vec{v}(t)\,dt + \vec{C}$, integrate to get a $+C$ constant vector, then substitute $t = 0$ to find $\vec{C} = \vec{r}(0) - [\text{integral at }t=0]$. The definite integral approach is cleaner and less error-prone, which is why it is preferred in physics.

---

**Q5: In Part B, what kind of real-world motion does $\vec{r}(t) = (t + 2t^2,\ \sin t - t,\ 2t)$ describe qualitatively?**

**A:** Each component tells part of the story. The $x$-motion ($t + 2t^2$) is like a car accelerating from an initial speed of 1 unit/time — it moves right and speeds up. The $y$-motion ($\sin t - t$) is like a pendulum on a slowly moving conveyor belt — it oscillates left and right but drifts steadily in the $-y$ direction. The $z$-motion ($2t$) is simple uniform motion upward at constant speed. Altogether it resembles a helical drift with oscillation — something like a charged particle moving through crossed electric and magnetic fields, where the particle simultaneously drifts, oscillates, and moves in a perpendicular direction.