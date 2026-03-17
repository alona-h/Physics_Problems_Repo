# Problem 3 – Elimination of Time and Interpretation of Acceleration

The path is given in parametric form:

$$
x(t) = 2t^2, \qquad y(t) = 3t^3
$$

---

## Question 3.1 – Eliminate the parameter $t$

**Question:** Find a direct relationship between $y$ and $x$, with no $t$ in it.

**Solution:**

**Step 1:** Start with the $x$ equation and solve for $t$:

$$
x = 2t^2
$$

$$
t^2 = \frac{x}{2}
$$

$$
t = \sqrt{\frac{x}{2}} = \left(\frac{x}{2}\right)^{1/2}
$$

**Step 2:** We need $t^3$ for the $y$ equation. Write $t^3 = t^2 \cdot t$:

$$
t^3 = t^2 \cdot t = \frac{x}{2} \cdot \left(\frac{x}{2}\right)^{1/2} = \left(\frac{x}{2}\right)^{3/2}
$$

**Step 3:** Substitute into $y = 3t^3$:

$$
y = 3\left(\frac{x}{2}\right)^{3/2}
$$

$$
\boxed{y = \frac{3}{2^{3/2}}\, x^{3/2} = \frac{3\sqrt{2}}{4}\, x^{3/2}}
$$

**Verification:** Simplifying $\dfrac{3}{2^{3/2}}$:

$$
2^{3/2} = 2 \cdot 2^{1/2} = 2\sqrt{2}, \qquad \frac{3}{2\sqrt{2}} = \frac{3}{2\sqrt{2}} \cdot \frac{\sqrt{2}}{\sqrt{2}} = \frac{3\sqrt{2}}{4}
$$

So the path equation is:

$$
y = \frac{3\sqrt{2}}{4}\, x^{3/2}
$$

This is valid for $x \geq 0$ (since $x = 2t^2 \geq 0$ always).

> **Explanation:**
> "Eliminating the parameter" means getting rid of $t$ so we can see the shape of the path directly as a curve on the $xy$-plane. The trick is to isolate $t$ (or a power of $t$) from one equation and substitute into the other. Here we got $y \propto x^{3/2}$, which is called a **power-law curve** — it looks like a parabola but grows a bit faster. Since $x = 2t^2$ is always non-negative, the curve only exists for $x \geq 0$, and it starts at the origin when $t = 0$.

---

## Question 3.2 – Draw the trajectory

**Question:** Describe the shape and key points of the curve $y = \frac{3\sqrt{2}}{4}x^{3/2}$.

**Solution:**

Compute a few points using $x(t) = 2t^2$ and $y(t) = 3t^3$:

| $t$ | $x = 2t^2$ | $y = 3t^3$ |
|:---:|:---:|:---:|
| $-2$ | $8$ | $-24$ |
| $-1$ | $2$ | $-3$ |
| $-0.5$ | $0.5$ | $-0.375$ |
| $0$ | $0$ | $0$ |
| $0.5$ | $0.5$ | $0.375$ |
| $1$ | $2$ | $3$ |
| $2$ | $8$ | $24$ |

**Key features of the trajectory:**
- Passes through the **origin** at $t = 0$
- For $t > 0$: the curve goes into the **upper right** quadrant ($x > 0$, $y > 0$)
- For $t < 0$: the curve goes into the **lower right** quadrant ($x > 0$, $y < 0$)
- The curve is **symmetric about the $x$-axis**: for $\pm t$, $x$ is the same but $y$ changes sign
- At the origin the curve has a **cusp** — a sharp point where the body momentarily stops
  (shown in next question: $|\vec{v}(0)| = 0$)

> **Explanation:**
> The trajectory looks like a sideways "S" curve lying in the right half of the plane, passing sharply through the origin. For positive times the body moves to the upper right; for negative times it was coming from the lower right. Notice that both $t = 1$ and $t = -1$ give the same $x = 2$ but opposite $y$ values ($+3$ and $-3$), confirming the mirror symmetry about the $x$-axis. The special point at the origin is a cusp — the body's speed is zero there, so the curve has a sharp corner instead of a smooth turn.

---

## Question 3.3 – Calculate $\vec{v}(t)$, $|\vec{v}(t)|$, $\vec{a}(t)$, and $|\vec{a}(t)|$

### Velocity vector $\vec{v}(t)$

**Solution:**

Differentiate each component with respect to $t$:

$$
v_x(t) = \frac{dx}{dt} = \frac{d}{dt}(2t^2) = 4t
$$

$$
v_y(t) = \frac{dy}{dt} = \frac{d}{dt}(3t^3) = 9t^2
$$

$$
\boxed{\vec{v}(t) = (4t,\ 9t^2)}
$$

### Magnitude of velocity $|\vec{v}(t)|$

$$
|\vec{v}(t)| = \sqrt{v_x^2 + v_y^2} = \sqrt{(4t)^2 + (9t^2)^2}
$$

$$
= \sqrt{16t^2 + 81t^4}
$$

Factor out $t^2$ from under the square root:

$$
= \sqrt{t^2(16 + 81t^2)} = |t|\sqrt{16 + 81t^2}
$$

$$
\boxed{|\vec{v}(t)| = |t|\sqrt{16 + 81t^2}}
$$

**Check at $t = 0$:**

$$
|\vec{v}(0)| = 0 \cdot \sqrt{16} = 0
$$

The body is instantaneously **at rest** at the origin — confirming the cusp.

### Acceleration vector $\vec{a}(t)$

Differentiate $\vec{v}(t)$:

$$
a_x(t) = \frac{dv_x}{dt} = \frac{d}{dt}(4t) = 4
$$

$$
a_y(t) = \frac{dv_y}{dt} = \frac{d}{dt}(9t^2) = 18t
$$

$$
\boxed{\vec{a}(t) = (4,\ 18t)}
$$

### Magnitude of acceleration $|\vec{a}(t)|$

$$
|\vec{a}(t)| = \sqrt{a_x^2 + a_y^2} = \sqrt{4^2 + (18t)^2}
$$

$$
\boxed{|\vec{a}(t)| = \sqrt{16 + 324t^2}}
$$

> **Explanation:**
> To find velocity, differentiate the position components with respect to time — one component at a time. The velocity vector $\vec{v}(t) = (4t, 9t^2)$ tells us the direction and speed the body is moving at each moment. Its magnitude $|\vec{v}|$ is found using the Pythagorean theorem on the two components, just like finding the length of an arrow on a graph. The acceleration vector is found the same way — differentiate velocity. Notice that $a_x = 4$ is constant, while $a_y = 18t$ grows with time.

---

## Question 3.4 – Is the acceleration constant?

**Question:** Does $\vec{a}(t)$ stay the same for all $t$?

**Solution:**

The acceleration vector is:

$$
\vec{a}(t) = (4,\ 18t)
$$

**Check each component:**

- $a_x = 4$ — this is **constant** (does not depend on $t$) ✓
- $a_y = 18t$ — this **depends on $t$** ✗

Since $a_y$ changes with time, the acceleration vector **changes direction and magnitude** over time.

**Conclusion:**

$$
\boxed{\vec{a}(t) \text{ is NOT constant}}
$$

**Example values:**

| $t$ | $\vec{a}(t)$ | $|\vec{a}(t)|$ |
|:---:|:---:|:---:|
| $-1$ | $(4,\ -18)$ | $\sqrt{16+324} \approx 18.4$ |
| $0$ | $(4,\ 0)$ | $4$ |
| $1$ | $(4,\ 18)$ | $\approx 18.4$ |
| $2$ | $(4,\ 36)$ | $\approx 36.2$ |

At $t = 0$ the acceleration points purely in the $x$-direction.
For $t \neq 0$ it tilts upward or downward and grows in magnitude.

> **Explanation:**
> A constant acceleration would mean both components — horizontal and vertical — are fixed numbers that never change. Here the horizontal acceleration $a_x = 4$ is indeed fixed, but the vertical acceleration $a_y = 18t$ grows over time. So while the "push" in the $x$-direction never changes, the "push" in the $y$-direction keeps increasing. This is fundamentally different from projectile motion (where $\vec{a} = (0, -g)$ is truly constant). The fact that $a_y$ changes means this motion cannot be decomposed into two simple uniform-acceleration problems.

---

## Possible Questions and Answers

**Q1: What is a parametric form of a curve, and why is it useful?**

A: A parametric form describes a curve using a third variable — the parameter $t$ (often time) — to express both $x$ and $y$ separately as functions of $t$. It is useful because it tells you not just the *shape* of the path but also *when* the body is at each point, and it can describe curves that loop back on themselves or have cusps, which a simple $y = f(x)$ formula cannot handle. Eliminating $t$ recovers the shape, but loses the timing information.

---

**Q2: What is a cusp, and why does one appear at the origin here?**

A: A cusp is a sharp point on a curve where the tangent direction reverses. It appears wherever the velocity vector $\vec{v}(t) = \vec{0}$, i.e. the body momentarily stops. Here $\vec{v}(0) = (0, 0)$, so at $t = 0$ the body is at rest. It arrives at the origin from one direction and then leaves in a different direction, creating a sharp corner in the path. If the speed were never zero, the curve would be smooth everywhere.

---

**Q3: How do you find the direction of motion (the angle of $\vec{v}$) at a given moment?**

A: The direction of velocity at time $t$ is given by the angle:
$$
\theta(t) = \arctan\!\left(\frac{v_y}{v_x}\right) = \arctan\!\left(\frac{9t^2}{4t}\right) = \arctan\!\left(\frac{9t}{4}\right) \quad (t \neq 0)
$$
At $t = 1$: $\theta = \arctan(9/4) \approx 66°$ above the horizontal.
At $t = -1$: $\theta = \arctan(-9/4) \approx -66°$ below the horizontal.
At $t = 0$ the direction is undefined (body is at rest — the cusp).

---

**Q4: Why is $|\vec{v}(t)| = |t|\sqrt{16 + 81t^2}$ and not just $t\sqrt{16 + 81t^2}$?**

A: Speed (magnitude of velocity) is always non-negative. When we factor $t^2$ out of the square root we get $\sqrt{t^2} = |t|$, not just $t$. For $t < 0$ the body is moving just as fast as for $t > 0$ (by symmetry), so the speed must be positive regardless of the sign of $t$. Writing $|t|$ instead of $t$ ensures this is always true.

---

**Q5: What is the difference between the acceleration being "constant in magnitude" vs "constant as a vector"?**

A: A constant *vector* means both magnitude and direction are fixed — every component is the same number for all $t$. A constant *magnitude* only means $|\vec{a}|$ stays the same, but the direction can still rotate. Here neither is true: $|\vec{a}(t)| = \sqrt{16 + 324t^2}$ grows with $t$, and the direction of $\vec{a}$ also changes because $a_y = 18t$ changes. So the acceleration is non-constant in both senses.