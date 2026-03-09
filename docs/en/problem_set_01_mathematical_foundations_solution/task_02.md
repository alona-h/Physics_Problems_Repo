# Problem Set 1 – Problem 2: Parametric Trajectory, Velocity, and Acceleration

---

## Setup

**Given parametric trajectory:**
$$\vec{r}(t) = \bigl(t^2,\ \sin t,\ 5\bigr)$$

This means the position of a point in 3D space at time $t$ is:
- $x$-coordinate: $t^2$
- $y$-coordinate: $\sin t$
- $z$-coordinate: $5$ (constant — the motion is confined to a horizontal plane at height 5)

> **Explanation:** A parametric trajectory describes where an object *is* at every moment in time. Instead of giving $y$ as a function of $x$ directly, we express both as functions of a third variable — the parameter $t$ (usually time). This is much more flexible, as it can describe curves that loop, spiral, or move in 3D in ways a standard $y = f(x)$ formula cannot.

---

## 2.1 – Velocity vector $\vec{v}(t) = \frac{d\vec{r}}{dt}$

Velocity is the **time derivative** of position — it tells us how fast and in what direction the object is moving at each moment. Each component is differentiated separately:

$$\vec{v}(t) = \frac{d\vec{r}}{dt} = \left(\frac{d}{dt}(t^2),\ \frac{d}{dt}(\sin t),\ \frac{d}{dt}(5)\right)$$

**Component by component:**

- $\frac{d}{dt}(t^2) = 2t$
- $\frac{d}{dt}(\sin t) = \cos t$
- $\frac{d}{dt}(5) = 0$ (constant has zero derivative)

$$\boxed{\vec{v}(t) = (2t,\ \cos t,\ 0)}$$

> **Explanation:** Velocity is a vector, not just a number — it encodes both *speed* (how fast) and *direction* (which way). Each component of the velocity vector tells you how quickly the object is moving along that axis. The $z$-component is 0 because the object never changes its height (it stays at $z = 5$ forever), so there is no vertical motion.

---

## 2.2 – Acceleration vector $\vec{a}(t) = \frac{d^2\vec{r}}{dt^2}$

Acceleration is the **time derivative of velocity** — it tells us how the velocity is changing:

$$\vec{a}(t) = \frac{d\vec{v}}{dt} = \left(\frac{d}{dt}(2t),\ \frac{d}{dt}(\cos t),\ \frac{d}{dt}(0)\right)$$

**Component by component:**

- $\frac{d}{dt}(2t) = 2$
- $\frac{d}{dt}(\cos t) = -\sin t$
- $\frac{d}{dt}(0) = 0$

$$\boxed{\vec{a}(t) = (2,\ -\sin t,\ 0)}$$

> **Explanation:** Just as velocity is the rate of change of position, acceleration is the rate of change of velocity. A non-zero acceleration means the object's velocity is changing — either its speed, its direction, or both. Here, the $x$-component of acceleration is a constant $2$, meaning the object accelerates uniformly in the $x$-direction (like a car pressing the gas at a steady rate). The $y$-component oscillates as $-\sin t$, meaning the object alternately accelerates and decelerates in the $y$-direction.

---

## 2.3 – Speed at $t = 1$: calculate $|\vec{v}(1)|$

First, evaluate the velocity vector at $t = 1$:

$$\vec{v}(1) = (2(1),\ \cos(1),\ 0) = (2,\ \cos 1,\ 0)$$

Using the numerical value $\cos 1 \approx 0.5403$:

$$\vec{v}(1) = (2,\ 0.5403,\ 0)$$

Now compute the magnitude:

$$|\vec{v}(1)| = \sqrt{(2)^2 + (\cos 1)^2 + 0^2} = \sqrt{4 + \cos^2(1)}$$

$$= \sqrt{4 + (0.5403)^2} = \sqrt{4 + 0.2919} = \sqrt{4.2919}$$

$$\boxed{|\vec{v}(1)| = \sqrt{4 + \cos^2 1} \approx 2.072}$$

> **Explanation:** The magnitude of the velocity vector gives the **speed** — a single positive number representing how fast the object is moving at that instant, regardless of direction. It is calculated the same way as the magnitude of any vector: square each component, sum them, take the square root. The $z$-component contributes nothing because motion is entirely in the $xy$-plane.

---

## 2.4 – Dot product $\vec{v} \cdot \vec{a}$

Using the general expressions $\vec{v}(t) = (2t, \cos t, 0)$ and $\vec{a}(t) = (2, -\sin t, 0)$:

$$\vec{v} \cdot \vec{a} = (2t)(2) + (\cos t)(-\sin t) + (0)(0)$$

$$= 4t - \cos t \sin t$$

Using the double-angle identity $\sin(2t) = 2\sin t \cos t$, so $\sin t \cos t = \frac{1}{2}\sin(2t)$:

$$\boxed{\vec{v} \cdot \vec{a} = 4t - \frac{1}{2}\sin(2t)}$$

**Physical meaning:** The dot product $\vec{v} \cdot \vec{a}$ equals $|\vec{v}| \cdot a_t$, where $a_t$ is the **tangential acceleration** — the component of acceleration that changes the object's *speed* (as opposed to direction). When $\vec{v} \cdot \vec{a} > 0$, the object is speeding up; when $< 0$, it is slowing down.

> **Explanation:** The dot product of velocity and acceleration is not just a number — it carries physical meaning. It tells you whether the object is speeding up or slowing down at any given moment. If velocity and acceleration point in the same general direction (angle < 90°), the dot product is positive and the object gains speed. If they point in opposing directions, the object loses speed. This is how a car coasts to a stop: acceleration (deceleration) is opposite to velocity, giving a negative dot product.

---

## 2.5 – Cross product $\vec{v} \times \vec{a}$

Using $\vec{v}(t) = (2t, \cos t, 0)$ and $\vec{a}(t) = (2, -\sin t, 0)$:

$$\vec{v} \times \vec{a} = \begin{vmatrix} \vec{i} & \vec{j} & \vec{k} \\ 2t & \cos t & 0 \\ 2 & -\sin t & 0 \end{vmatrix}$$

Expanding along the first row:

$$= \vec{i}\bigl[(\cos t)(0) - (0)(-\sin t)\bigr] - \vec{j}\bigl[(2t)(0) - (0)(2)\bigr] + \vec{k}\bigl[(2t)(-\sin t) - (\cos t)(2)\bigr]$$

- $\vec{i}$-component: $0 - 0 = 0$
- $\vec{j}$-component: $-(0 - 0) = 0$
- $\vec{k}$-component: $-2t\sin t - 2\cos t$

$$\boxed{\vec{v} \times \vec{a} = \bigl(0,\ 0,\ -2t\sin t - 2\cos t\bigr)}$$

**Physical meaning:** The magnitude of $\vec{v} \times \vec{a}$ is related to the **normal acceleration** (centripetal acceleration) by:

$$|\vec{v} \times \vec{a}| = |\vec{v}|^2 \cdot \kappa = |\vec{v}| \cdot a_n$$

where $\kappa$ is the curvature of the trajectory. A larger cross product magnitude means the path is bending more sharply.

The result is purely in the $\vec{k}$ direction (pointing along the $z$-axis), which makes sense: since all motion occurs in the $xy$-plane, the "rotation" axis must be perpendicular to it, i.e. along $z$.

> **Explanation:** The cross product of velocity and acceleration gives a vector perpendicular to the plane of motion. Its magnitude tells you how sharply the path is curving — this is the geometric counterpart of the dot product. While $\vec{v} \cdot \vec{a}$ captures changes in *speed*, $\vec{v} \times \vec{a}$ captures changes in *direction*. Together they give a complete picture of how the motion is evolving.

---

## Summary Table

| Quantity | Expression | Value at $t=1$ (approx) |
|---|---|---|
| $\vec{r}(t)$ | $(t^2,\ \sin t,\ 5)$ | $(1,\ 0.841,\ 5)$ |
| $\vec{v}(t)$ | $(2t,\ \cos t,\ 0)$ | $(2,\ 0.540,\ 0)$ |
| $\vec{a}(t)$ | $(2,\ -\sin t,\ 0)$ | $(2,\ -0.841,\ 0)$ |
| $|\vec{v}(1)|$ | $\sqrt{4 + \cos^2 1}$ | $\approx 2.072$ |
| $\vec{v} \cdot \vec{a}$ | $4t - \frac{1}{2}\sin(2t)$ | $\approx 3.546$ |
| $\vec{v} \times \vec{a}$ | $(0,\ 0,\ -2t\sin t - 2\cos t)$ | $(0,\ 0,\ -2.764)$ |

---

## 5 Possible Questions & Answers

---

**Q1: Why is the $z$-component of velocity zero throughout the entire motion?**

**A:** Because the $z$-component of the position is the constant $5$, i.e. $z(t) = 5$ for all $t$. Differentiating a constant gives zero: $\frac{d}{dt}(5) = 0$. Physically, this means the object never moves vertically — it is permanently confined to the horizontal plane $z = 5$. No matter how the object moves in $x$ and $y$, the absence of any $z$-variation means no vertical velocity component.

---

**Q2: What is the physical difference between $\vec{v} \cdot \vec{a}$ and $\vec{v} \times \vec{a}$?**

**A:** The dot product $\vec{v} \cdot \vec{a}$ measures the **tangential** component of acceleration — the part that changes the object's *speed*. When $\vec{v} \cdot \vec{a} > 0$ the object speeds up; when $< 0$ it slows down. The cross product $\vec{v} \times \vec{a}$ captures the **normal** component — the part that changes the object's *direction* without affecting speed. Together they decompose acceleration into "how fast am I going?" and "which way am I turning?"

---

**Q3: At what time $t$ does the object have zero acceleration in the $y$-direction?**

**A:** The $y$-component of acceleration is $a_y(t) = -\sin t$. This equals zero when $\sin t = 0$, which occurs at $t = 0, \pi, 2\pi, \ldots$ — i.e. at integer multiples of $\pi$. At these moments, the velocity in the $y$-direction is momentarily neither increasing nor decreasing (it is at a local maximum or minimum of $\cos t$).

---

**Q4: Is the speed $|\vec{v}(t)|$ constant? What would it imply if it were?**

**A:** No, the speed is not constant. $|\vec{v}(t)| = \sqrt{4t^2 + \cos^2 t}$, which clearly depends on $t$ — for instance, at $t = 0$ we get $|\vec{v}(0)| = \sqrt{0 + 1} = 1$, while at $t = 1$ we get $\approx 2.072$. If the speed *were* constant, it would mean $\vec{v} \cdot \vec{a} = 0$ at all times — the velocity and acceleration would always be perpendicular. This happens in uniform circular motion, where acceleration only changes direction, never speed.

---

**Q5: What does the direction of $\vec{v} \times \vec{a}$ tell us physically?**

**A:** The direction of $\vec{v} \times \vec{a}$ points along the **axis of curvature** — perpendicular to the plane in which the path is instantaneously bending. In our case it always points along $\pm\vec{k}$ (the $z$-axis), which confirms the motion is entirely within the $z = 5$ plane. The sign tells us the sense of rotation: a negative $z$-component (as at $t = 1$, where we get $\approx -2.764$) means the path is curving in the clockwise direction when viewed from above.