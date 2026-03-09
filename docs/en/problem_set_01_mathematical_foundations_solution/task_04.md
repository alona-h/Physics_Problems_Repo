# Problem Set 1 – Problem 4: Geometry of Parametric Curves

---

## Overview

A **parametric curve** describes a path in space by expressing coordinates as functions of a parameter $t$ (usually time). Instead of a single equation like $y = f(x)$, we have separate equations for each coordinate. This section investigates four classic curves, identifying their geometric shape, computing velocity and acceleration, and checking whether speed or magnitude of acceleration is constant.

> **Key idea:** For each curve we will:
> 1. **Eliminate the parameter** — combine $x(t)$ and $y(t)$ to get a single equation in $x$ and $y$ only, revealing the shape
> 2. **Identify the curve type** — circle, ellipse, parabola, hyperbola, etc.
> 3. **Compute $\vec{v}(t)$ and $\vec{a}(t)$** — differentiate each component
> 4. **Check constancy of $|\vec{v}|$ and $|\vec{a}|$** — does the speed or acceleration magnitude stay the same for all $t$?

---

## Curve A: $x(t) = R\cos t, \quad y(t) = R\sin t$

---

### A.1 – Eliminate the parameter

We use the fundamental Pythagorean identity: $\cos^2 t + \sin^2 t = 1$.

From the parametric equations:
$$\cos t = \frac{x}{R}, \qquad \sin t = \frac{y}{R}$$

Squaring both and adding:
$$\cos^2 t + \sin^2 t = \frac{x^2}{R^2} + \frac{y^2}{R^2} = 1$$

$$\boxed{x^2 + y^2 = R^2}$$

### A.2 – Type of curve

This is the equation of a **circle** centred at the origin with radius $R$.

> **Explanation:** As $t$ goes from $0$ to $2\pi$, the point $(R\cos t, R\sin t)$ traces out a full circle of radius $R$. At $t=0$ you are at $(R, 0)$ — the rightmost point. At $t = \pi/2$ you are at $(0, R)$ — the top. At $t = \pi$ you are at $(-R, 0)$ — the leftmost point. The motion is counterclockwise and repeats every $2\pi$.

---

### A.3 – Velocity and acceleration

**Velocity** — differentiate each component:
$$\vec{v}(t) = \frac{d}{dt}(R\cos t,\ R\sin t) = (-R\sin t,\ R\cos t)$$

**Acceleration** — differentiate velocity:
$$\vec{a}(t) = \frac{d}{dt}(-R\sin t,\ R\cos t) = (-R\cos t,\ -R\sin t)$$

Notice that:
$$\vec{a}(t) = -\vec{r}(t)$$

This is the hallmark of circular motion: the acceleration always points **toward the centre** (centripetal acceleration).

> **Explanation:** The velocity vector $(-R\sin t, R\cos t)$ is always perpendicular to the position vector $(R\cos t, R\sin t)$ — you can verify this by computing their dot product: $(-R\sin t)(R\cos t) + (R\cos t)(R\sin t) = 0$. This makes perfect sense geometrically: on a circle, the direction of motion (tangent) is always at right angles to the radius.

---

### A.4 – Constancy of $|\vec{v}|$ and $|\vec{a}|$

**Speed:**
$$|\vec{v}(t)| = \sqrt{(-R\sin t)^2 + (R\cos t)^2} = \sqrt{R^2\sin^2 t + R^2\cos^2 t} = R\sqrt{\sin^2 t + \cos^2 t} = R$$

$$\boxed{|\vec{v}| = R = \text{const}}$$

**Acceleration magnitude:**
$$|\vec{a}(t)| = \sqrt{(-R\cos t)^2 + (-R\sin t)^2} = \sqrt{R^2\cos^2 t + R^2\sin^2 t} = R$$

$$\boxed{|\vec{a}| = R = \text{const}}$$

> **Explanation:** Both speed and acceleration magnitude are constant — this is the definition of **uniform circular motion**. Even though the *direction* of both vectors changes continuously, their sizes never change. The constant centripetal acceleration $|\vec{a}| = R$ (with angular frequency $\omega = 1$ here) continuously redirects the velocity without ever speeding up or slowing down the object. In general, for angular frequency $\omega$, the centripetal acceleration would be $R\omega^2$.

---

## Curve B: $x(t) = a\cos t, \quad y(t) = b\sin t$

---

### B.1 – Eliminate the parameter

From the parametric equations:
$$\cos t = \frac{x}{a}, \qquad \sin t = \frac{y}{b}$$

Squaring and adding, using $\cos^2 t + \sin^2 t = 1$:

$$\frac{x^2}{a^2} + \frac{y^2}{b^2} = 1$$

$$\boxed{\frac{x^2}{a^2} + \frac{y^2}{b^2} = 1}$$

### B.2 – Type of curve

This is the equation of an **ellipse** centred at the origin with semi-axes $a$ (along $x$) and $b$ (along $y$).

> **Explanation:** An ellipse is a "stretched circle." If $a = b = R$, the formula reduces to Curve A (a circle). When $a \neq b$, the circle is stretched along one axis. The parameter $a$ gives the half-width and $b$ gives the half-height. As $t$ goes from $0$ to $2\pi$, the point traces the full ellipse counterclockwise.

---

### B.3 – Velocity and acceleration

**Velocity:**
$$\vec{v}(t) = \frac{d}{dt}(a\cos t,\ b\sin t) = (-a\sin t,\ b\cos t)$$

**Acceleration:**
$$\vec{a}(t) = \frac{d}{dt}(-a\sin t,\ b\cos t) = (-a\cos t,\ -b\sin t)$$

Again we can write $\vec{a}(t) = -(a\cos t, b\sin t) = -\vec{r}(t)$, so the acceleration still points toward the origin — but because $a \neq b$, it is no longer purely centripetal in the circular sense.

---

### B.4 – Constancy of $|\vec{v}|$ and $|\vec{a}|$

**Speed:**
$$|\vec{v}(t)| = \sqrt{a^2\sin^2 t + b^2\cos^2 t}$$

This depends on $t$ (unless $a = b$), so:

$$\boxed{|\vec{v}| \neq \text{const} \quad \text{(unless } a = b\text{)}}$$

For example, at $t = 0$: $|\vec{v}| = \sqrt{0 + b^2} = b$. At $t = \pi/2$: $|\vec{v}| = \sqrt{a^2 + 0} = a$. These differ when $a \neq b$.

**Acceleration magnitude:**
$$|\vec{a}(t)| = \sqrt{a^2\cos^2 t + b^2\sin^2 t}$$

This also depends on $t$ (unless $a = b$):

$$\boxed{|\vec{a}| \neq \text{const} \quad \text{(unless } a = b\text{)}}$$

> **Explanation:** Unlike the circle, an ellipse does not have uniform speed. The object moves *fastest* when it passes through the ends of the *minor* (shorter) axis, and *slowest* at the ends of the *major* (longer) axis. This is directly analogous to Kepler's second law of planetary motion: a planet on an elliptical orbit moves faster when closer to the Sun and slower when farther away.

---

## Curve C: $x(t) = t, \quad y(t) = t^2$

---

### C.1 – Eliminate the parameter

Since $x = t$, we can directly substitute $t = x$ into $y = t^2$:

$$y = x^2$$

$$\boxed{y = x^2}$$

### C.2 – Type of curve

This is a **parabola** opening upward, with vertex at the origin.

> **Explanation:** This is the simplest elimination: the parameter $t$ equals $x$ directly, so we just replace $t$ with $x$ everywhere. As $t$ increases from $-\infty$ to $+\infty$, the point $(t, t^2)$ traces the parabola from bottom-left, through the vertex at $(0,0)$, to bottom-right. The object's $x$-position increases linearly with $t$, while its $y$-position grows quadratically.

---

### C.3 – Velocity and acceleration

**Velocity:**
$$\vec{v}(t) = \frac{d}{dt}(t,\ t^2) = (1,\ 2t)$$

**Acceleration:**
$$\vec{a}(t) = \frac{d}{dt}(1,\ 2t) = (0,\ 2)$$

The acceleration is a **constant vector** pointing upward in the $y$-direction.

> **Explanation:** This is analogous to projectile motion (but with axes swapped). A constant upward acceleration of $2$ in the $y$-direction combined with constant horizontal velocity of $1$ produces a parabolic path — exactly as a ball thrown horizontally follows a parabolic arc under constant gravitational acceleration.

---

### C.4 – Constancy of $|\vec{v}|$ and $|\vec{a}|$

**Speed:**
$$|\vec{v}(t)| = \sqrt{1^2 + (2t)^2} = \sqrt{1 + 4t^2}$$

This grows without bound as $t \to \pm\infty$:

$$\boxed{|\vec{v}| \neq \text{const}}$$

**Acceleration magnitude:**
$$|\vec{a}(t)| = \sqrt{0^2 + 2^2} = 2$$

$$\boxed{|\vec{a}| = 2 = \text{const}}$$

> **Explanation:** The acceleration is constant (both in direction and magnitude) — it always pushes the object upward with strength $2$. The speed, however, grows with time: as the object moves further along the parabola, the upward velocity component $2t$ keeps increasing, making the object move faster and faster. This is exactly how a ball accelerates downward under gravity while also moving horizontally.

---

## Curve D: $x(t) = \cosh t, \quad y(t) = \sinh t$

---

### D.1 – Eliminate the parameter

We use the **hyperbolic identity**: $\cosh^2 t - \sinh^2 t = 1$.

From the parametric equations:
$$\cosh t = x, \qquad \sinh t = y$$

Substituting into the identity:
$$x^2 - y^2 = 1$$

$$\boxed{x^2 - y^2 = 1}$$

### D.2 – Type of curve

This is the equation of a **hyperbola** (right branch only, since $\cosh t \geq 1 > 0$ for all $t$).

> **Explanation of hyperbolic functions:** The hyperbolic cosine and sine are defined as:
> $$\cosh t = \frac{e^t + e^{-t}}{2}, \qquad \sinh t = \frac{e^t - e^{-t}}{2}$$
> They are analogous to circular $\cos$ and $\sin$, but instead of parameterising a circle ($x^2 + y^2 = 1$), they parameterise a hyperbola ($x^2 - y^2 = 1$). Since $\cosh t \geq 1$ always, only the *right branch* ($x \geq 1$) of the hyperbola is traced. As $t \to +\infty$, the point moves up and to the right along the asymptote $y = x$.

---

### D.3 – Velocity and acceleration

We use the derivatives of hyperbolic functions:
$$\frac{d}{dt}\cosh t = \sinh t, \qquad \frac{d}{dt}\sinh t = \cosh t$$

**Velocity:**
$$\vec{v}(t) = \frac{d}{dt}(\cosh t,\ \sinh t) = (\sinh t,\ \cosh t)$$

**Acceleration:**
$$\vec{a}(t) = \frac{d}{dt}(\sinh t,\ \cosh t) = (\cosh t,\ \sinh t)$$

Notice that $\vec{a}(t) = \vec{r}(t)$ — the acceleration points *away* from the origin (contrast with the circle/ellipse where $\vec{a} = -\vec{r}$, pointing *toward* the origin).

> **Explanation:** On a circle, the acceleration points inward (centripetal). On a hyperbola, the "force" points outward — this reflects the repulsive or saddle-point nature of hyperbolic motion. This type of acceleration arises, for example, in the motion of a charged particle repelled by another charge of the same sign.

---

### D.4 – Constancy of $|\vec{v}|$ and $|\vec{a}|$

**Speed:**
$$|\vec{v}(t)| = \sqrt{\sinh^2 t + \cosh^2 t}$$

Using the identity $\cosh^2 t + \sinh^2 t = \cosh(2t)$:

$$|\vec{v}(t)| = \sqrt{\cosh(2t)}$$

Since $\cosh(2t)$ increases as $|t|$ grows, this is not constant:

$$\boxed{|\vec{v}| \neq \text{const}}$$

**Acceleration magnitude:**
$$|\vec{a}(t)| = \sqrt{\cosh^2 t + \sinh^2 t} = \sqrt{\cosh(2t)}$$

$$\boxed{|\vec{a}| \neq \text{const}}$$

Note that $|\vec{v}| = |\vec{a}|$ at every moment, even though neither is constant.

> **Explanation:** Unlike the circle (where both $|\vec{v}|$ and $|\vec{a}|$ are constant), the hyperbola has neither constant speed nor constant acceleration magnitude. As the object moves further along the curve, both grow exponentially. This is because $\cosh t \approx \sinh t \approx \frac{e^t}{2}$ for large $t$ — both grow exponentially, so the speed explodes as $t \to \infty$.

---

## Summary Table

| | **Curve A** | **Curve B** | **Curve C** | **Curve D** |
|---|---|---|---|---|
| **Parametric form** | $x = R\cos t$ $y = R\sin t$ | $x = a\cos t$ $y = b\sin t$ | $x = t$ $y = t^2$ | $x = \cosh t$ $y = \sinh t$ |
| **Cartesian equation** | $x^2 + y^2 = R^2$ | $\dfrac{x^2}{a^2}+\dfrac{y^2}{b^2}=1$ | $y = x^2$ | $x^2 - y^2 = 1$ |
| **Curve type** | Circle | Ellipse | Parabola | Hyperbola (right branch) |
| **$\vec{v}(t)$** | $(-R\sin t,\ R\cos t)$ | $(-a\sin t,\ b\cos t)$ | $(1,\ 2t)$ | $(\sinh t,\ \cosh t)$ |
| **$\vec{a}(t)$** | $(-R\cos t,\ -R\sin t)$ | $(-a\cos t,\ -b\sin t)$ | $(0,\ 2)$ | $(\cosh t,\ \sinh t)$ |
| **$\|\vec{v}(t)\|$** | $\sqrt{R^2\sin^2 t + R^2\cos^2 t} = R$ | $\sqrt{a^2\sin^2 t + b^2\cos^2 t}$ | $\sqrt{1 + 4t^2}$ | $\sqrt{\cosh(2t)}$ |
| **$\|\vec{a}(t)\|$** | $\sqrt{R^2\cos^2 t + R^2\sin^2 t} = R$ | $\sqrt{a^2\cos^2 t + b^2\sin^2 t}$ | $\sqrt{0^2 + 2^2} = 2$ | $\sqrt{\cosh(2t)}$ |
| **$\|\vec{v}\| = \text{const}$?** | ✓ Yes, $= R$ | ✗ No | ✗ No | ✗ No |
| **$\|\vec{a}\| = \text{const}$?** | ✓ Yes, $= R$ | ✗ No | ✓ Yes, $= 2$ | ✗ No |
| **Special note** | $\vec{a} = -\vec{r}$ (centripetal) | $\vec{a} = -\vec{r}$ (non-uniform) | $\vec{a}$ constant vector | $\vec{a} = +\vec{r}$ (centrifugal); $\|\vec{v}\| = \|\vec{a}\|$ always |

---

## 5 Possible Questions & Answers

---

**Q1: What is the key identity used for curves A and B, and why does the same approach not work for the parabola (Curve C)?**

**A:** For curves A and B, we exploit the Pythagorean identity $\cos^2 t + \sin^2 t = 1$. By writing $\cos t = x/R$ and $\sin t = y/R$ (or with $a$, $b$), squaring both, and adding, the parameter $t$ vanishes entirely. This works because both components involve the same trigonometric functions related by the Pythagorean identity. For the parabola (Curve C), $x(t) = t$ means the parameter $t$ *is* $x$ — so elimination is trivially done by direct substitution ($y = t^2 = x^2$), with no identity needed.

---

**Q2: What is the geometric relationship between the velocity vector and the curve at any point?**

**A:** The velocity vector $\vec{v}(t)$ is always **tangent** to the curve at the corresponding point. This is true for *any* parametric curve — differentiation gives the direction of motion, which is by definition tangential to the path. For a circle (Curve A), you can verify this explicitly: the position vector $(R\cos t, R\sin t)$ points radially outward, and the velocity $(-R\sin t, R\cos t)$ is perpendicular to it (dot product $= 0$), confirming it is tangential.

---

**Q3: Why does Curve A have both constant speed and constant acceleration magnitude, while Curve B (which is just a stretched circle) does not?**

**A:** A circle has perfect rotational symmetry — every point on it is the same distance from the centre, so the curvature is uniform everywhere and the object travels equal arc lengths in equal times. An ellipse is asymmetric: the curvature is tighter at the ends of the minor axis and flatter at the ends of the major axis. Because the path bends differently at different points, the object must speed up and slow down to maintain consistent parametrisation by $t$, resulting in variable speed and variable acceleration magnitude.

---

**Q4: What is the difference between $\cosh$ and $\cos$? Why does one give a circle and the other a hyperbola?**

**A:** Circular functions ($\cos t$, $\sin t$) satisfy $\cos^2 t + \sin^2 t = 1$ — the sum of squares equals 1, giving a circle. Hyperbolic functions ($\cosh t$, $\sinh t$) satisfy $\cosh^2 t - \sinh^2 t = 1$ — the *difference* of squares equals 1, giving a hyperbola. The underlying difference is that circular functions arise from the unit circle $e^{it}$ in the complex plane, while hyperbolic functions arise from real exponentials: $\cosh t = (e^t + e^{-t})/2$, $\sinh t = (e^t - e^{-t})/2$. The sign difference (plus vs minus) is what geometrically separates the circle from the hyperbola.

---

**Q5: For Curve C (the parabola), the acceleration is constant. What does this imply physically?**

**A:** A constant acceleration vector means a constant force is acting on the object (by Newton's second law $\vec{F} = m\vec{a}$). In Curve C, $\vec{a} = (0, 2)$ — a constant upward force. This is exactly the situation of **projectile motion** under gravity (but with the $y$-axis flipped, since gravity acts downward). The horizontal component of velocity is constant (no horizontal force), while the vertical velocity grows linearly. The parabolic path is a direct consequence of having one direction with constant acceleration and another with zero acceleration — a fundamental result in classical mechanics.