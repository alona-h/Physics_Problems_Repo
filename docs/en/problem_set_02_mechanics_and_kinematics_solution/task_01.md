# Problem 1 – Uniform and Uniformly Accelerated Motion

The equation of motion is given:

$$
x(t) = x_0 + v_0 t + \frac{1}{2} a t^2
$$

---

## Question 1.1 – Determine the velocity $v(t)$ and acceleration $a(t)$

**Solution:**

Velocity is the first derivative of position with respect to time:

$$
v(t) = \frac{dx}{dt} = \frac{d}{dt}\left(x_0 + v_0 t + \frac{1}{2}a t^2\right)
$$

Differentiating term by term:
- $\frac{d}{dt}(x_0) = 0$ (constant)
- $\frac{d}{dt}(v_0 t) = v_0$
- $\frac{d}{dt}\!\left(\frac{1}{2}a t^2\right) = at$

$$
\boxed{v(t) = v_0 + at}
$$

Acceleration is the first derivative of velocity (or the second derivative of position):

$$
a(t) = \frac{dv}{dt} = \frac{d}{dt}(v_0 + at)
$$

- $\frac{d}{dt}(v_0) = 0$ (constant)
- $\frac{d}{dt}(at) = a$

$$
\boxed{a(t) = a = \text{const}}
$$

> **Explanation:**
> Think of position $x(t)$ as describing *where* something is at time $t$. Velocity tells you *how fast* the position is changing — so you find it by differentiating $x(t)$. Acceleration tells you *how fast the velocity is changing* — so you differentiate $v(t)$ once more. Notice that the acceleration $a$ turns out to be just a constant number, which makes sense: "uniformly accelerated" literally means the acceleration doesn't change over time.

---

## Question 1.2 – Numerical calculations for $x_0 = 0$, $v_0 = 5\ \text{m/s}$, $a = -2\ \text{m/s}^2$

With these values the equations become:

$$
x(t) = 5t - t^2, \qquad v(t) = 5 - 2t, \qquad a(t) = -2\ \text{m/s}^2
$$

---

### 1.2a – Stopping time

**Question:** When does the body stop (i.e. when is $v(t) = 0$)?

**Solution:**

Set $v(t) = 0$:

$$
v_0 + at = 0
$$

$$
5 + (-2)t = 0
$$

$$
5 - 2t = 0
$$

$$
t = \frac{5}{2} = 2.5\ \text{s}
$$

$$
\boxed{t_{\text{stop}} = 2.5\ \text{s}}
$$

> **Explanation:**
> The body starts moving at $5\ \text{m/s}$ but is being slowed down by the negative acceleration (think of it as a braking force). Every second, the velocity drops by $2\ \text{m/s}$. After $2.5$ seconds the velocity reaches exactly zero — the body has stopped. Note: it doesn't *stay* stopped; if the force continues, the body would start moving backwards.

---

### 1.2b – Maximum velocity depending on time and the sign of acceleration

**Solution:**

The velocity function is:

$$
v(t) = v_0 + at
$$

This is a linear function of time. Its behaviour depends on the sign of $a$:

**Case 1: $a > 0$ (positive acceleration)**
- $v(t)$ increases without bound as $t \to \infty$
- The maximum velocity over a finite interval $[0, T]$ is at $t = T$:

$$
v_{\max} = v_0 + aT
$$

**Case 2: $a < 0$ (negative acceleration) — our case**
- $v(t)$ decreases over time
- The maximum velocity is at $t = 0$:

$$
v_{\max} = v_0 = 5\ \text{m/s}
$$

- After $t_{\text{stop}} = 2.5\ \text{s}$, the velocity becomes negative (body moves in the opposite direction)

**Case 3: $a = 0$ (uniform motion)**
- $v(t) = v_0 = \text{const}$ — velocity is constant at all times

$$
\boxed{v_{\max} = v_0 = 5\ \text{m/s} \quad (\text{at } t = 0, \text{ for } a < 0)}
$$

> **Explanation:**
> Because the acceleration is negative (like a car braking), the body starts at its fastest and slows down from there. The highest speed is therefore right at the start, $t = 0$. If instead the acceleration were positive (like a car speeding up), the body would get faster and faster, and there would be no maximum unless you set a time limit. The sign of $a$ completely controls whether the object is speeding up or slowing down.

---

### 1.2c – Maximum displacement

**Question:** How far does the body travel before it stops?

**Solution:**

The body reaches maximum displacement at the stopping time $t_{\text{stop}} = 2.5\ \text{s}$ (because after this point it moves backwards, reducing $x$).

Substituting into $x(t)$:

$$
x_{\max} = x(t_{\text{stop}}) = x_0 + v_0\, t_{\text{stop}} + \frac{1}{2}a\, t_{\text{stop}}^2
$$

$$
x_{\max} = 0 + 5 \cdot 2.5 + \frac{1}{2}(-2)(2.5)^2
$$

$$
x_{\max} = 12.5 + \frac{1}{2}(-2)(6.25)
$$

$$
x_{\max} = 12.5 - 6.25
$$

$$
\boxed{x_{\max} = 6.25\ \text{m}}
$$

Alternatively, using the kinematic formula $v^2 = v_0^2 + 2a\,\Delta x$ and setting $v = 0$:

$$
0 = v_0^2 + 2a\,x_{\max}
$$

$$
x_{\max} = -\frac{v_0^2}{2a} = -\frac{25}{2 \cdot (-2)} = \frac{25}{4} = 6.25\ \text{m}
$$

> **Explanation:**
> The body moves forward while $v > 0$, i.e. until $t = 2.5\ \text{s}$. After that it starts going backwards, so the *furthest point* it ever reaches is at exactly $t = 2.5\ \text{s}$. Plugging that time into the position formula gives $6.25\ \text{m}$. An easy way to remember: "maximum displacement happens when velocity is zero."

---

## Question 1.3 – Visualize $x(t)$, $v(t)$, $a(t)$

Below is a description of the three graphs for $x_0=0$, $v_0=5\ \text{m/s}$, $a=-2\ \text{m/s}^2$:

**Position $x(t) = 5t - t^2$**
- Parabola opening downward
- Starts at $x = 0$, rises to a maximum of $6.25\ \text{m}$ at $t = 2.5\ \text{s}$, then decreases

| $t\ (\text{s})$ | $x\ (\text{m})$ |
|:-:|:-:|
| 0 | 0 |
| 1 | 4 |
| 2 | 6 |
| 2.5 | 6.25 |
| 3 | 6 |
| 4 | 4 |
| 5 | 0 |

**Velocity $v(t) = 5 - 2t$**
- Straight line with negative slope
- Starts at $v = 5\ \text{m/s}$, crosses zero at $t = 2.5\ \text{s}$, becomes negative afterward

| $t\ (\text{s})$ | $v\ (\text{m/s})$ |
|:-:|:-:|
| 0 | 5 |
| 1 | 3 |
| 2 | 1 |
| 2.5 | 0 |
| 3 | −1 |
| 4 | −3 |

**Acceleration $a(t) = -2\ \text{m/s}^2$**
- Horizontal line at $a = -2\ \text{m/s}^2$ for all $t$

> **Explanation:**
> The three graphs tell the full story of the motion. The position graph ($x$) looks like an upside-down parabola — the body moves forward, slows to a stop, then turns around. The velocity graph ($v$) is a straight line going downhill — it starts positive, shrinks to zero, then goes negative (backwards motion). The acceleration graph is just a flat horizontal line — the acceleration never changes, which is the defining feature of *uniformly accelerated* motion.

---

## Possible Questions and Answers

**Q1: What is the physical meaning of a negative acceleration when the initial velocity is positive?**

A: A negative acceleration means the acceleration vector points in the opposite direction to the motion. When $v_0 > 0$ and $a < 0$, the body is decelerating — it slows down, stops, and then (if the force continues) accelerates in the negative direction. In everyday language, this is braking.

---

**Q2: What is the difference between deceleration and negative acceleration?**

A: "Deceleration" informally means the speed (magnitude of velocity) is decreasing. "Negative acceleration" simply means the acceleration vector points in the negative direction. They are the same when the body is moving in the positive direction, but if the body is already moving in the negative direction, a negative acceleration actually *speeds it up*.

---

**Q3: Why is the maximum displacement found at $t_{\text{stop}}$ and not at a later time?**

A: Because for $t > t_{\text{stop}}$ the velocity is negative, meaning the body moves in the $-x$ direction and the position $x(t)$ decreases. The position is largest when $v = 0$, i.e. at $t_{\text{stop}} = 2.5\ \text{s}$.

---

**Q4: How does the kinematic formula $v^2 = v_0^2 + 2a\Delta x$ follow from $x(t)$ and $v(t)$?**

A: From $v(t) = v_0 + at$ we get $t = \frac{v - v_0}{a}$. Substituting into $x(t) = x_0 + v_0 t + \frac{1}{2}at^2$ and simplifying yields $v^2 = v_0^2 + 2a(x - x_0)$. This formula is useful because it eliminates time entirely.

---

**Q5: What happens to $x(t)$ as $t \to \infty$ for $a < 0$?**

A: Since $x(t) = x_0 + v_0 t + \frac{1}{2}at^2$ and $a < 0$, the $\frac{1}{2}at^2$ term dominates for large $t$ and drives $x(t) \to -\infty$. The body eventually moves infinitely far in the negative direction. In a real physical scenario (e.g. a car), the braking force would stop being applied once the car halts, but mathematically with constant $a < 0$ the motion continues in reverse forever.