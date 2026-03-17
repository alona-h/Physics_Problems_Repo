# Problem 7 – 2D Motion with a Given Acceleration

Given:
- Acceleration: $\vec{a} = (2,\ -3)$ (constant, in m/s²)
- Initial velocity: $\vec{v}(0) = (1,\ 0)$ (in m/s)
- Initial position: $\vec{r}(0) = (0,\ 0)$ (at the origin)

---

## Question 7.1 – Determine $\vec{v}(t)$

**Question:** Find the velocity vector at every time $t$, given the constant
acceleration and the initial velocity.

**Solution:**

Since acceleration is the derivative of velocity, velocity is the
**integral of acceleration**. For a constant acceleration vector
$\vec{a} = (a_x,\ a_y)$:

$$
\vec{v}(t) = \vec{v}(0) + \int_0^t \vec{a}\, dt'
$$

Integrate each component separately:

**$x$-component:**

$$
v_x(t) = v_x(0) + \int_0^t a_x\, dt' = v_x(0) + a_x \cdot t
$$

$$
v_x(t) = 1 + 2t
$$

**$y$-component:**

$$
v_y(t) = v_y(0) + \int_0^t a_y\, dt' = v_y(0) + a_y \cdot t
$$

$$
v_y(t) = 0 + (-3)t = -3t
$$

$$
\boxed{\vec{v}(t) = (1 + 2t,\ -3t)}
$$

**Verification — check initial condition:**

At $t = 0$:
$$
\vec{v}(0) = (1 + 0,\ 0) = (1,\ 0) \checkmark
$$

**Verification — check derivative:**

$$
\frac{d\vec{v}}{dt} = \frac{d}{dt}(1 + 2t,\ -3t) = (2,\ -3) = \vec{a} \checkmark
$$

> **Explanation:**
> If you know how fast something is accelerating, you can find its velocity
> by integrating (the reverse of differentiating). For a constant acceleration,
> this is straightforward: velocity just grows linearly with time. The formula
> $\vec{v}(t) = \vec{v}(0) + \vec{a}\,t$ is the vector version of the familiar
> $v = v_0 + at$ from Problem 1. We apply it independently to each component —
> the $x$-direction and $y$-direction are treated completely separately, just
> as in projectile motion. The $x$-velocity starts at $1$ m/s and grows because
> $a_x = +2$ m/s². The $y$-velocity starts at $0$ and becomes increasingly
> negative because $a_y = -3$ m/s² (like gravity pulling downward, but stronger).

---

## Question 7.2 – Determine $\vec{r}(t)$

**Question:** Find the position vector at every time $t$, given the velocity
and the initial position.

**Solution:**

Position is the **integral of velocity**:

$$
\vec{r}(t) = \vec{r}(0) + \int_0^t \vec{v}(t')\, dt'
$$

Integrate each component of $\vec{v}(t) = (1 + 2t,\ -3t)$:

**$x$-component:**

$$
x(t) = x(0) + \int_0^t (1 + 2t')\, dt'
$$

$$
= 0 + \left[t' + t'^2\right]_0^t
$$

$$
= t + t^2 - 0
$$

$$
x(t) = t + t^2
$$

**$y$-component:**

$$
y(t) = y(0) + \int_0^t (-3t')\, dt'
$$

$$
= 0 + \left[-\frac{3t'^2}{2}\right]_0^t
$$

$$
= -\frac{3t^2}{2} - 0
$$

$$
y(t) = -\frac{3}{2}t^2
$$

$$
\boxed{\vec{r}(t) = \left(t + t^2,\ -\frac{3}{2}t^2\right)}
$$

**Verification — check initial condition:**

At $t = 0$:
$$
\vec{r}(0) = (0 + 0,\ 0) = (0,\ 0) \checkmark
$$

**Verification — check derivative:**

$$
\frac{d\vec{r}}{dt} = \frac{d}{dt}\!\left(t + t^2,\ -\frac{3}{2}t^2\right) = (1 + 2t,\ -3t) = \vec{v}(t) \checkmark
$$

**Numerical table of position over time:**

| $t\ (\text{s})$ | $x = t + t^2\ (\text{m})$ | $y = -\frac{3}{2}t^2\ (\text{m})$ |
|:---:|:---:|:---:|
| $0$ | $0$ | $0$ |
| $0.5$ | $0.75$ | $-0.375$ |
| $1$ | $2$ | $-1.5$ |
| $1.5$ | $3.75$ | $-3.375$ |
| $2$ | $6$ | $-6$ |
| $3$ | $12$ | $-13.5$ |

> **Explanation:**
> Position is found by integrating velocity — again the reverse of
> differentiation. For each component we simply integrate a polynomial in $t$:
> integrating $1$ gives $t$, integrating $2t$ gives $t^2$, integrating $-3t$
> gives $-\frac{3}{2}t^2$. The result is the standard kinematic formula applied
> to each direction independently:
> $$x(t) = x_0 + v_{x0}t + \tfrac{1}{2}a_x t^2 = 0 + 1\cdot t + \tfrac{1}{2}\cdot 2\cdot t^2 = t + t^2$$
> $$y(t) = y_0 + v_{y0}t + \tfrac{1}{2}a_y t^2 = 0 + 0\cdot t + \tfrac{1}{2}\cdot(-3)\cdot t^2 = -\tfrac{3}{2}t^2$$
> The motion in $x$ is a mix of constant-speed and accelerating components.
> The motion in $y$ is pure downward acceleration from rest — exactly like a
> free-falling object with $g = 3$ m/s² instead of $9.81$ m/s².

---

## Question 7.3 – Draw the trajectory, velocity vector, and acceleration vector

**Question:** Describe and analyze the shape of the trajectory, and show where
the velocity and acceleration vectors point at selected moments in time.

### Shape of the trajectory

**Eliminating $t$ to find $y$ as a function of $x$:**

We have:
$$
x = t + t^2, \qquad y = -\frac{3}{2}t^2
$$

From the $y$ equation, solve for $t^2$:

$$
y = -\frac{3}{2}t^2 \implies t^2 = -\frac{2y}{3}
$$

From the $x$ equation:
$$
x = t + t^2 = t - \frac{2y}{3}
$$

Solve for $t$:
$$
t = x + \frac{2y}{3}
$$

Now substitute back into $t^2 = -\dfrac{2y}{3}$:

$$
\left(x + \frac{2y}{3}\right)^2 = -\frac{2y}{3}
$$

Expand the left side:

$$
x^2 + \frac{4xy}{3} + \frac{4y^2}{9} = -\frac{2y}{3}
$$

Rearranging (bringing all terms to one side):

$$
x^2 + \frac{4xy}{3} + \frac{4y^2}{9} + \frac{2y}{3} = 0
$$

This is a **parabolic curve** in the $xy$-plane (a quadratic relation between
$x$ and $y$).

### Vectors at selected moments

**At $t = 0$:**

$$
\vec{r}(0) = (0,\ 0)
$$
$$
\vec{v}(0) = (1,\ 0) \quad \text{— points purely to the right}
$$
$$
\vec{a}(0) = (2,\ -3) \quad \text{— points right and downward}
$$

Angle of $\vec{v}(0)$: $\theta_v = \arctan(0/1) = 0°$ (horizontal)

Angle of $\vec{a}$: $\theta_a = \arctan(-3/2) \approx -56.3°$ (below horizontal)

---

**At $t = 1$:**

$$
\vec{r}(1) = (2,\ -1.5)
$$
$$
\vec{v}(1) = (3,\ -3) \quad \text{— points right and downward at } 45°
$$
$$
\vec{a}(1) = (2,\ -3) \quad \text{— same as always (constant)}
$$

Speed at $t = 1$:
$$
|\vec{v}(1)| = \sqrt{3^2 + (-3)^2} = \sqrt{9 + 9} = 3\sqrt{2} \approx 4.24\ \text{m/s}
$$

Angle of $\vec{v}(1)$: $\theta = \arctan(-3/3) = -45°$

---

**At $t = 2$:**

$$
\vec{r}(2) = (6,\ -6)
$$
$$
\vec{v}(2) = (5,\ -6)
$$
$$
\vec{a}(2) = (2,\ -3)
$$

Speed at $t = 2$:
$$
|\vec{v}(2)| = \sqrt{25 + 36} = \sqrt{61} \approx 7.81\ \text{m/s}
$$

Angle of $\vec{v}(2)$: $\theta = \arctan(-6/5) \approx -50.2°$

---

**Summary table:**

| $t$ | Position $(x, y)$ | $\vec{v}(t)$ | $|\vec{v}|$ | $\vec{a}(t)$ |
|:---:|:---:|:---:|:---:|:---:|
| $0$ | $(0,\ 0)$ | $(1,\ 0)$ | $1$ | $(2,\ -3)$ |
| $1$ | $(2,\ -1.5)$ | $(3,\ -3)$ | $3\sqrt{2} \approx 4.24$ | $(2,\ -3)$ |
| $2$ | $(6,\ -6)$ | $(5,\ -6)$ | $\sqrt{61} \approx 7.81$ | $(2,\ -3)$ |
| $3$ | $(12,\ -13.5)$ | $(7,\ -9)$ | $\sqrt{130} \approx 11.4$ | $(2,\ -3)$ |

### Key observations about the trajectory:

- The body starts at the origin moving **purely horizontally** to the right
- It curves **downward and to the right** due to the acceleration
- The acceleration arrow $(2, -3)$ is the same at every point —
  constant acceleration
- The velocity arrow rotates clockwise over time (the motion tilts
  increasingly downward) and grows in magnitude
- The path is a **parabola** (quadratic relationship between $x$ and $y$),
  exactly like projectile motion but with a non-vertical acceleration

> **Explanation:**
> The trajectory is a parabola — the same type of curve as in projectile motion
> (Problem 2). This is always the case when the acceleration is constant: two
> integrations of a constant give a quadratic (degree 2) polynomial in $t$,
> which traces a parabola in the plane. The velocity arrow at each point is
> tangent to the curve — it shows the direction of travel. The acceleration
> arrow always points in the same fixed direction $(2, -3)$, regardless of where
> the body is or how fast it is going. Notice how the velocity arrow starts
> horizontal and gradually rotates toward the direction of the acceleration —
> the body is being "pulled" in the direction of $\vec{a}$ more and more
> as time goes on.

---

## Possible Questions and Answers

**Q1: Why can we integrate each component of $\vec{a}$ independently to find $\vec{v}$,
and each component of $\vec{v}$ independently to find $\vec{r}$?**

A: Because the $x$ and $y$ directions are completely independent in Newtonian
mechanics. The acceleration in the $x$-direction only affects the $x$-velocity
and $x$-position; it has no effect on the $y$-components, and vice versa. This
is the same principle used in projectile motion (Problem 2): horizontal and
vertical motions are treated separately. Mathematically, a vector equation
$\frac{d\vec{v}}{dt} = \vec{a}$ is just two scalar equations — one for each
component — and they can be solved independently.

---

**Q2: How do you verify that your answers for $\vec{v}(t)$ and $\vec{r}(t)$
are correct?**

A: There are two checks for each:

For $\vec{v}(t)$: (1) differentiate it and confirm you get $\vec{a} = (2, -3)$;
(2) substitute $t = 0$ and confirm you get $\vec{v}(0) = (1, 0)$.

For $\vec{r}(t)$: (1) differentiate it and confirm you get $\vec{v}(t) = (1+2t, -3t)$;
(2) substitute $t = 0$ and confirm you get $\vec{r}(0) = (0, 0)$.

Both checks together guarantee the solution is correct — it satisfies the
differential equation and the initial conditions.

---

**Q3: The trajectory looks like a parabola. How would you prove this rigorously?**

A: A parabola is a curve described by a quadratic equation. We showed that:
$$
y = -\frac{3}{2}t^2 \quad \text{and} \quad x = t + t^2
$$
From $y$: $t^2 = -2y/3$, and from $x$: $t = x - t^2 = x + 2y/3$.
Substituting $t = x + 2y/3$ into $t^2 = -2y/3$ gives the equation
$(x + 2y/3)^2 = -2y/3$, which is a quadratic equation in $x$ and $y$.
Any curve described by a quadratic equation of this form (where the
highest-degree terms form a perfect square) is a parabola.

---

**Q4: At what time does the body reach its maximum $x$-velocity, and does the
$x$-velocity ever stop increasing?**

A: The $x$-velocity is $v_x(t) = 1 + 2t$. Since $a_x = 2 > 0$ is constant and
positive, $v_x$ increases indefinitely — it never stops growing. There is no
maximum. The body accelerates in the $x$-direction forever (in this model).
Similarly, the $y$-velocity $v_y(t) = -3t$ becomes more and more negative
without bound. This is a consequence of having a constant, non-zero acceleration
with no opposing forces (no friction, no air resistance, no spring force) in
the model.

---

**Q5: How does this problem differ from projectile motion (Problem 2),
and what do they have in common?**

A: **In common:** Both have constant acceleration, so both produce parabolic
trajectories. Both use the same kinematic formulas
$\vec{v}(t) = \vec{v}(0) + \vec{a}t$ and
$\vec{r}(t) = \vec{r}(0) + \vec{v}(0)t + \frac{1}{2}\vec{a}t^2$.
Both are solved by treating $x$ and $y$ components independently.

**Differences:** In projectile motion the acceleration is purely vertical
$(0, -g)$ with zero horizontal acceleration. Here the acceleration has both
horizontal ($a_x = 2$) and vertical ($a_y = -3$) components. In projectile
motion the horizontal velocity is constant; here it grows over time. The
parabola in projectile motion opens downward along the vertical; here it is
tilted because the acceleration is diagonal.