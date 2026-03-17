# Problem 4 – Circular Motion

A body moves in a circle of radius $R$ with angular velocity $\omega$.

---

## Question 4.1 – Determine $\vec{r}(t)$, $\vec{v}(t)$, $\vec{a}(t)$

### Position vector $\vec{r}(t)$

**Question:** Write down the position of the body at time $t$.

**Solution:**

A body moving in a circle of radius $R$ sweeps out an angle $\theta(t) = \omega t$
measured from the positive $x$-axis. Using basic trigonometry (the $x$ and $y$
coordinates of a point on a circle):

$$
x(t) = R\cos(\omega t), \qquad y(t) = R\sin(\omega t)
$$

$$
\boxed{\vec{r}(t) = \bigl(R\cos(\omega t),\ R\sin(\omega t)\bigr)}
$$

> **Explanation:**
> Imagine a point moving around the edge of a circle. At any moment its horizontal
> position is $R\cos(\omega t)$ and its vertical position is $R\sin(\omega t)$ — this
> is just the definition of cosine and sine on a circle of radius $R$. The angle
> $\omega t$ grows steadily with time because $\omega$ (angular velocity) tells you
> how many radians per second the body sweeps. One full circle is $2\pi$ radians, so
> the body completes one revolution every $T = 2\pi/\omega$ seconds.

---

### Velocity vector $\vec{v}(t)$

**Question:** Find the velocity by differentiating $\vec{r}(t)$.

**Solution:**

Differentiate each component of $\vec{r}(t)$ with respect to $t$:

$$
v_x(t) = \frac{dx}{dt} = \frac{d}{dt}\bigl[R\cos(\omega t)\bigr]
$$

Using the chain rule: $\frac{d}{dt}\cos(\omega t) = -\omega\sin(\omega t)$:

$$
v_x(t) = -R\omega\sin(\omega t)
$$

$$
v_y(t) = \frac{dy}{dt} = \frac{d}{dt}\bigl[R\sin(\omega t)\bigr]
$$

Using the chain rule: $\frac{d}{dt}\sin(\omega t) = \omega\cos(\omega t)$:

$$
v_y(t) = R\omega\cos(\omega t)
$$

$$
\boxed{\vec{v}(t) = \bigl(-R\omega\sin(\omega t),\ R\omega\cos(\omega t)\bigr)}
$$

> **Explanation:**
> Velocity is always the derivative of position. We differentiate $\cos(\omega t)$
> and $\sin(\omega t)$ using the chain rule — the $\omega$ "comes down" as a
> multiplier each time. Notice the pattern: differentiating cosine gives
> $-\sin$, and differentiating sine gives $+\cos$. The factor $R\omega$ out front
> controls the speed. The negative sign in $v_x$ is not a mistake — it means
> that when the body is at the rightmost point of the circle ($\cos = 1$,
> $\sin = 0$), the velocity points purely upward ($v_x = 0$, $v_y = R\omega$),
> which is exactly what we would expect: the body is moving tangentially.

---

### Acceleration vector $\vec{a}(t)$

**Question:** Find the acceleration by differentiating $\vec{v}(t)$.

**Solution:**

Differentiate each component of $\vec{v}(t)$:

$$
a_x(t) = \frac{dv_x}{dt} = \frac{d}{dt}\bigl[-R\omega\sin(\omega t)\bigr]
$$

Using the chain rule: $\frac{d}{dt}\sin(\omega t) = \omega\cos(\omega t)$:

$$
a_x(t) = -R\omega \cdot \omega\cos(\omega t) = -R\omega^2\cos(\omega t)
$$

$$
a_y(t) = \frac{dv_y}{dt} = \frac{d}{dt}\bigl[R\omega\cos(\omega t)\bigr]
$$

Using the chain rule: $\frac{d}{dt}\cos(\omega t) = -\omega\sin(\omega t)$:

$$
a_y(t) = R\omega \cdot (-\omega\sin(\omega t)) = -R\omega^2\sin(\omega t)
$$

$$
\boxed{\vec{a}(t) = \bigl(-R\omega^2\cos(\omega t),\ -R\omega^2\sin(\omega t)\bigr)}
$$

> **Explanation:**
> We differentiate velocity the same way we differentiated position. Each
> differentiation brings down another factor of $\omega$ and flips sine/cosine.
> The crucial observation is that both components of $\vec{a}(t)$ have a
> **minus sign** compared to $\vec{r}(t)$. We will use this in Question 4.3
> to show that the acceleration always points back toward the center of the
> circle — this is called centripetal acceleration.

---

## Question 4.2 – Determine $|\vec{r}(t)|$, $|\vec{v}(t)|$, $|\vec{a}(t)|$

**Question:** Calculate the magnitudes (lengths) of the three vectors.

### Magnitude of position $|\vec{r}(t)|$

$$
|\vec{r}(t)| = \sqrt{x^2 + y^2} = \sqrt{R^2\cos^2(\omega t) + R^2\sin^2(\omega t)}
$$

Factor out $R^2$:

$$
= \sqrt{R^2\bigl(\cos^2(\omega t) + \sin^2(\omega t)\bigr)}
$$

Using the Pythagorean identity $\cos^2\theta + \sin^2\theta = 1$:

$$
= \sqrt{R^2 \cdot 1} = R
$$

$$
\boxed{|\vec{r}(t)| = R = \text{const}}
$$

### Magnitude of velocity $|\vec{v}(t)|$

$$
|\vec{v}(t)| = \sqrt{v_x^2 + v_y^2}
= \sqrt{(-R\omega\sin(\omega t))^2 + (R\omega\cos(\omega t))^2}
$$

$$
= \sqrt{R^2\omega^2\sin^2(\omega t) + R^2\omega^2\cos^2(\omega t)}
$$

$$
= \sqrt{R^2\omega^2\bigl(\sin^2(\omega t) + \cos^2(\omega t)\bigr)}
$$

$$
= \sqrt{R^2\omega^2 \cdot 1}
$$

$$
\boxed{|\vec{v}(t)| = R\omega = \text{const}}
$$

### Magnitude of acceleration $|\vec{a}(t)|$

$$
|\vec{a}(t)| = \sqrt{a_x^2 + a_y^2}
= \sqrt{(-R\omega^2\cos(\omega t))^2 + (-R\omega^2\sin(\omega t))^2}
$$

$$
= \sqrt{R^2\omega^4\cos^2(\omega t) + R^2\omega^4\sin^2(\omega t)}
$$

$$
= \sqrt{R^2\omega^4\bigl(\cos^2(\omega t) + \sin^2(\omega t)\bigr)}
$$

$$
= \sqrt{R^2\omega^4 \cdot 1}
$$

$$
\boxed{|\vec{a}(t)| = R\omega^2 = \text{const}}
$$

> **Explanation:**
> All three magnitudes are constants — they do not change with time. This makes
> perfect sense physically: the body stays on a circle of fixed radius $R$
> (so distance from center never changes), moves at fixed speed $R\omega$ (uniform
> circular motion), and always has the same centripetal acceleration $R\omega^2$
> pulling it inward. The key mathematical tool used in all three calculations is
> the Pythagorean identity $\sin^2\theta + \cos^2\theta = 1$, which "cancels out"
> the time dependence every time.

---

## Question 4.3 – Show that the acceleration is centripetal

**Question:** Prove that $\vec{a}(t)$ always points toward the center of the circle.

**Solution:**

Compare $\vec{a}(t)$ and $\vec{r}(t)$ side by side:

$$
\vec{r}(t) = \bigl(R\cos(\omega t),\ R\sin(\omega t)\bigr)
$$

$$
\vec{a}(t) = \bigl(-R\omega^2\cos(\omega t),\ -R\omega^2\sin(\omega t)\bigr)
$$

Factor $-\omega^2$ out of $\vec{a}(t)$:

$$
\vec{a}(t) = -\omega^2 \bigl(R\cos(\omega t),\ R\sin(\omega t)\bigr)
$$

$$
\boxed{\vec{a}(t) = -\omega^2\,\vec{r}(t)}
$$

**What this means:**

- The acceleration vector is **proportional** to the position vector
- The **minus sign** means it points in the **opposite direction** to $\vec{r}(t)$
- Since $\vec{r}(t)$ always points **outward** from the center to the body,
  $\vec{a}(t)$ always points **inward** — toward the center
- This is exactly the definition of **centripetal** (from Latin: *centrum* = center,
  *petere* = to seek)

**Alternative check using the dot product** (perpendicularity of $\vec{v}$ and $\vec{a}$):

$$
\vec{v}(t) \cdot \vec{a}(t) = (-R\omega\sin)(-R\omega^2\cos) + (R\omega\cos)(-R\omega^2\sin)
$$

$$
= R^2\omega^3\sin\cos - R^2\omega^3\cos\sin = 0
$$

So $\vec{v} \perp \vec{a}$ at all times — the acceleration has no component along
the direction of motion, only perpendicular to it (toward the center). This confirms
there is no tangential acceleration, only centripetal.

> **Explanation:**
> "Centripetal" means "directed toward the center." The elegant result
> $\vec{a} = -\omega^2\vec{r}$ tells us that at every instant the acceleration
> arrow points from the body straight back to the center of the circle — no matter
> where on the circle the body is. This is what keeps the body on its circular path:
> instead of flying off in a straight line (which it would do if there were no
> force), the centripetal acceleration constantly pulls it inward. In real life this
> inward force could be tension in a string, gravity (for orbiting satellites),
> or friction (for a car turning a corner).

---

## Question 4.4 – Visualize the vectors $\vec{r}$, $\vec{v}$, $\vec{a}$

**Question:** Describe how the three vectors look at a typical point on the circle.

**Solution:**

Choose a specific moment, e.g. $t = 0$:

$$
\vec{r}(0) = (R,\ 0) \quad \longrightarrow \quad \text{points right (along +x axis)}
$$

$$
\vec{v}(0) = (0,\ R\omega) \quad \longrightarrow \quad \text{points up (along +y axis)}
$$

$$
\vec{a}(0) = (-R\omega^2,\ 0) \quad \longrightarrow \quad \text{points left (along -x axis, toward center)}
$$

**Key geometric relationships at every point on the circle:**

| Vector | Direction | Magnitude | Changes direction? |
|:---|:---|:---|:---|
| $\vec{r}$ | Radially outward (center → body) | $R$ | Yes (rotates) |
| $\vec{v}$ | Tangential (perpendicular to $\vec{r}$) | $R\omega$ | Yes (rotates) |
| $\vec{a}$ | Radially inward (body → center) | $R\omega^2$ | Yes (rotates) |

**Mutual angles:**
- $\vec{r}$ and $\vec{v}$: always **perpendicular** ($90°$) — velocity is always tangent to the circle
- $\vec{v}$ and $\vec{a}$: always **perpendicular** ($90°$)
- $\vec{r}$ and $\vec{a}$: always **antiparallel** ($180°$) — they point in exactly opposite directions

All three vectors rotate together as the body moves around the circle, maintaining
these fixed angles between them at all times.

> **Explanation:**
> Picture the body as a dot moving around a clock face. The position arrow $\vec{r}$
> always points from the center outward to the dot — like the hand of a clock.
> The velocity arrow $\vec{v}$ is always a $90°$ turn from $\vec{r}$, pointing
> in the direction the dot is currently heading — tangent to the circle (like a
> tangent line just touching the circle at that point). The acceleration arrow
> $\vec{a}$ points straight back toward the center — opposite to $\vec{r}$. All
> three arrows rotate smoothly as the body goes around, always keeping these
> same $90°$ and $180°$ relationships to each other.

---

## Possible Questions and Answers

**Q1: What is angular velocity $\omega$ and how does it relate to the period $T$
and frequency $f$?**

A: Angular velocity $\omega$ measures how fast the body sweeps out angle, in
radians per second. One full revolution is $2\pi$ radians and takes time $T$
(the period), so:
$$
\omega = \frac{2\pi}{T} = 2\pi f
$$
where $f = 1/T$ is the frequency in Hz (revolutions per second). For example,
if a body completes one revolution per second ($f = 1\ \text{Hz}$), then
$\omega = 2\pi \approx 6.28\ \text{rad/s}$.

---

**Q2: The speed $|\vec{v}| = R\omega$ is constant, yet the acceleration is
non-zero. How is that possible?**

A: Acceleration is the rate of change of the **velocity vector**, not just its
magnitude (speed). Even though the speed never changes, the **direction** of
$\vec{v}$ changes continuously as the body goes around the circle. A changing
direction of velocity means there is acceleration. This acceleration changes the
direction of motion (keeps the body on the circle) rather than changing the speed.
This is why it has no component along $\vec{v}$ — it only acts perpendicular to it.

---

**Q3: What provides the centripetal force in real physical situations?**

A: Centripetal acceleration $a_c = R\omega^2 = v^2/R$ requires a net inward force
$F_c = ma_c$. What provides this force depends on the situation:
- **String/rope**: tension in the string (e.g. a ball on a string)
- **Gravity**: gravitational attraction (e.g. Moon orbiting Earth)
- **Friction**: static friction between tyre and road (e.g. car turning a corner)
- **Normal force**: component of normal force on a banked road
Without this inward force the body would travel in a straight line (Newton's first law).

---

**Q4: How does centripetal acceleration $|\vec{a}| = R\omega^2$ depend on $R$
and $\omega$ separately?**

A: For fixed $\omega$: doubling $R$ doubles the acceleration (linear dependence).
For fixed $R$: doubling $\omega$ quadruples the acceleration (quadratic dependence).
Equivalently, using speed $v = R\omega$:
$$
|\vec{a}| = \frac{v^2}{R}
$$
So for fixed speed $v$, a smaller radius means larger acceleration — a tighter
circle requires a stronger inward pull. This is why sharp bends are more dangerous
at high speeds.

---

**Q5: In what sense does $\vec{a} = -\omega^2 \vec{r}$ resemble simple harmonic motion?**

A: In simple harmonic motion (SHM) the equation of motion is $\ddot{x} = -\omega^2 x$,
meaning the acceleration is proportional to displacement and directed back toward
equilibrium. The result $\vec{a}(t) = -\omega^2\vec{r}(t)$ has exactly the same
structure in two dimensions. In fact, if you look at just the $x$-component of
circular motion: $x(t) = R\cos(\omega t)$, you get $\ddot{x} = -\omega^2 x$ —
which is the equation of SHM. Circular motion is therefore equivalent to two
perpendicular SHMs of the same frequency and amplitude, $90°$ out of phase with
each other.