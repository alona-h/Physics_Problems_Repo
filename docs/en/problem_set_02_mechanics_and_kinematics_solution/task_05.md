# Problem 5 – Elliptical Motion (Purely Kinematic)

The path is given in parametric form:

$$
x(t) = a\cos(\omega t), \qquad y(t) = b\sin(\omega t)
$$

where $a$ and $b$ are the semi-axes of the ellipse and $\omega$ is the angular frequency.

---

## Question 5.1 – Calculate the velocity and acceleration

### Velocity vector $\vec{v}(t)$

**Question:** Find $\vec{v}(t)$ by differentiating the position components.

**Solution:**

Differentiate $x(t)$ with respect to $t$ using the chain rule:

$$
v_x(t) = \frac{dx}{dt} = \frac{d}{dt}\bigl[a\cos(\omega t)\bigr]
$$

$$
v_x(t) = a \cdot (-\sin(\omega t)) \cdot \omega
$$

$$
v_x(t) = -a\omega\sin(\omega t)
$$

Differentiate $y(t)$ with respect to $t$:

$$
v_y(t) = \frac{dy}{dt} = \frac{d}{dt}\bigl[b\sin(\omega t)\bigr]
$$

$$
v_y(t) = b \cdot \cos(\omega t) \cdot \omega
$$

$$
v_y(t) = b\omega\cos(\omega t)
$$

$$
\boxed{\vec{v}(t) = \bigl(-a\omega\sin(\omega t),\ b\omega\cos(\omega t)\bigr)}
$$

### Acceleration vector $\vec{a}(t)$

**Question:** Find $\vec{a}(t)$ by differentiating $\vec{v}(t)$.

**Solution:**

Differentiate $v_x(t)$:

$$
a_x(t) = \frac{dv_x}{dt} = \frac{d}{dt}\bigl[-a\omega\sin(\omega t)\bigr]
$$

$$
a_x(t) = -a\omega \cdot \cos(\omega t) \cdot \omega
$$

$$
a_x(t) = -a\omega^2\cos(\omega t)
$$

Differentiate $v_y(t)$:

$$
a_y(t) = \frac{dv_y}{dt} = \frac{d}{dt}\bigl[b\omega\cos(\omega t)\bigr]
$$

$$
a_y(t) = b\omega \cdot (-\sin(\omega t)) \cdot \omega
$$

$$
a_y(t) = -b\omega^2\sin(\omega t)
$$

$$
\boxed{\vec{a}(t) = \bigl(-a\omega^2\cos(\omega t),\ -b\omega^2\sin(\omega t)\bigr)}
$$

**Key observation — link between $\vec{a}(t)$ and $\vec{r}(t)$:**

Notice that:

$$
\vec{r}(t) = \bigl(a\cos(\omega t),\ b\sin(\omega t)\bigr)
$$

$$
\vec{a}(t) = \bigl(-a\omega^2\cos(\omega t),\ -b\omega^2\sin(\omega t)\bigr) = -\omega^2\bigl(a\cos(\omega t),\ b\sin(\omega t)\bigr)
$$

$$
\boxed{\vec{a}(t) = -\omega^2\,\vec{r}(t)}
$$

The acceleration always points **toward the origin** (center of the ellipse),
with magnitude proportional to the distance from the center.

> **Explanation:**
> Differentiating position gives velocity, and differentiating velocity gives
> acceleration — the same procedure as in all previous problems. The chain rule
> brings down the factor $\omega$ each time we differentiate $\cos(\omega t)$ or
> $\sin(\omega t)$. After two differentiations we have $\omega^2$ and both
> components have flipped sign. The beautiful result $\vec{a} = -\omega^2\vec{r}$
> tells us the acceleration always points from the body back toward the center of
> the ellipse — similar to circular motion, but now the strength of the pull
> depends on *where* on the ellipse the body is, because $|\vec{r}|$ varies
> around an ellipse (unlike a circle where it is always $R$).

---

## Question 5.2 – Is the magnitude of the velocity constant?

**Question:** Does $|\vec{v}(t)|$ stay the same for all $t$, or does it change?

**Solution:**

Calculate the magnitude using the Pythagorean theorem:

$$
|\vec{v}(t)| = \sqrt{v_x^2 + v_y^2}
= \sqrt{(-a\omega\sin(\omega t))^2 + (b\omega\cos(\omega t))^2}
$$

Square each term:

$$
= \sqrt{a^2\omega^2\sin^2(\omega t) + b^2\omega^2\cos^2(\omega t)}
$$

Factor out $\omega^2$:

$$
= \omega\sqrt{a^2\sin^2(\omega t) + b^2\cos^2(\omega t)}
$$

$$
\boxed{|\vec{v}(t)| = \omega\sqrt{a^2\sin^2(\omega t) + b^2\cos^2(\omega t)}}
$$

**Is this constant?**

For this to be constant, the expression under the square root must not depend on $t$.
That requires $a^2 = b^2$, i.e. $a = b$.

- If $a = b = R$: the ellipse becomes a **circle**, and
  $|\vec{v}| = \omega\sqrt{R^2(\sin^2 + \cos^2)} = R\omega = \text{const}$ ✓
- If $a \neq b$: the expression $a^2\sin^2(\omega t) + b^2\cos^2(\omega t)$
  oscillates between $b^2$ (at $\omega t = 0$) and $a^2$ (at $\omega t = \pi/2$) ✗

$$
\boxed{|\vec{v}(t)| \text{ is NOT constant when } a \neq b}
$$

**Extreme values of $|\vec{v}(t)|$:**

The expression under the root is:

$$
f(t) = a^2\sin^2(\omega t) + b^2\cos^2(\omega t)
$$

Using $\sin^2 = 1 - \cos^2$:

$$
f(t) = a^2(1-\cos^2(\omega t)) + b^2\cos^2(\omega t) = a^2 + (b^2 - a^2)\cos^2(\omega t)
$$

- **Maximum of $f$**: when $\cos^2(\omega t) = 1$, i.e. $\omega t = 0, \pi, \ldots$
  (body at the ends of the $x$-axis, $x = \pm a$, $y = 0$):

$$
f_{\max} = a^2 + (b^2 - a^2) \cdot 1 = b^2 \quad \Rightarrow \quad |\vec{v}|_{\max} = \omega b
\quad \text{if } b > a
$$

- **Minimum of $f$**: when $\cos^2(\omega t) = 0$, i.e. $\omega t = \pi/2, 3\pi/2, \ldots$
  (body at the ends of the $y$-axis, $x = 0$, $y = \pm b$):

$$
f_{\min} = a^2 \quad \Rightarrow \quad |\vec{v}|_{\min} = \omega a
\quad \text{if } a < b
$$

In general (assuming $a > b$):

$$
|\vec{v}|_{\min} = \omega b \quad \text{(at the tips of the long axis)}
$$
$$
|\vec{v}|_{\max} = \omega a \quad \text{(at the tips of the short axis)}
$$

> **Explanation:**
> In circular motion the speed is constant because all points on the circle are
> the same distance from the center, so the body always "feels" the same pull.
> On an ellipse the body is sometimes closer to the center and sometimes farther
> away. When it is at the narrow ends (tips of the short axis), it is closest and
> moves fastest. When it is at the wide ends (tips of the long axis), it is
> farthest and moves slowest. This is the same behaviour as planets orbiting the
> Sun — they speed up when close to the Sun (perihelion) and slow down when far
> away (aphelion), which is Kepler's second law.

---

## Question 5.3 – Where is the velocity maximum?

**Question:** At what points on the ellipse does the body move fastest?

**Solution:**

From the analysis above, $|\vec{v}(t)|$ is maximum when $f(t)$ is maximum.

**Case $a > b$ (wider ellipse along $x$-axis):**

$$
f(t) = a^2 + (b^2 - a^2)\cos^2(\omega t)
$$

Since $b^2 - a^2 < 0$, $f(t)$ is maximum when $\cos^2(\omega t) = 0$:

$$
\omega t = \frac{\pi}{2} + n\pi, \quad n = 0, 1, 2, \ldots
$$

At these moments:

$$
x = a\cos\!\left(\frac{\pi}{2}\right) = 0, \qquad y = b\sin\!\left(\frac{\pi}{2}\right) = \pm b
$$

The body is at the **tips of the short axis**: $(0, +b)$ and $(0, -b)$

$$
|\vec{v}|_{\max} = \omega a
$$

**Case $b > a$ (taller ellipse along $y$-axis):**

$f(t)$ is maximum when $\cos^2(\omega t) = 1$, i.e. at $(+a, 0)$ and $(-a, 0)$:

$$
|\vec{v}|_{\max} = \omega b
$$

**Summary:**

$$
\boxed{|\vec{v}| \text{ is maximum at the tips of the \textbf{shorter} semi-axis}}
$$

The general rule: **speed is maximum where the ellipse is most curved** (the narrow ends).

> **Explanation:**
> Think of a ball rolling inside an oval bowl. It goes fastest at the tightest
> bends (narrow ends) and slowest at the widest, gentlest bends. For the ellipse
> $x = a\cos(\omega t)$, $y = b\sin(\omega t)$, the velocity has components from
> both $\sin$ and $\cos$. At the tip of the short axis ($y = \pm b$), the entire
> velocity is horizontal — $v_x = \mp a\omega$, $v_y = 0$ — and its magnitude
> $a\omega$ is greatest (for $a > b$). At the tip of the long axis ($x = \pm a$),
> only the vertical component remains — $v_x = 0$, $v_y = \pm b\omega$ — and its
> magnitude $b\omega$ is smallest.

---

## Question 5.4 – Draw the trajectory and graphs of $|\vec{v}(t)|$ and $|\vec{a}(t)|$

### The trajectory

**Eliminating $t$ to find the curve shape:**

From the parametric equations:

$$
\frac{x}{a} = \cos(\omega t), \qquad \frac{y}{b} = \sin(\omega t)
$$

Square both sides and add:

$$
\left(\frac{x}{a}\right)^2 + \left(\frac{y}{b}\right)^2 = \cos^2(\omega t) + \sin^2(\omega t) = 1
$$

$$
\boxed{\frac{x^2}{a^2} + \frac{y^2}{b^2} = 1}
$$

This is the **standard equation of an ellipse** centered at the origin,
with semi-axis $a$ along $x$ and semi-axis $b$ along $y$.

**Key points on the trajectory (for $a = 3$, $b = 2$, $\omega = 1$ as an example):**

| $t$ | $x = 3\cos t$ | $y = 2\sin t$ | Position description |
|:---:|:---:|:---:|:---|
| $0$ | $3$ | $0$ | Right tip of long axis |
| $\pi/2$ | $0$ | $2$ | Top tip of short axis |
| $\pi$ | $-3$ | $0$ | Left tip of long axis |
| $3\pi/2$ | $0$ | $-2$ | Bottom tip of short axis |
| $2\pi$ | $3$ | $0$ | Back to start (one full period) |

### Graph of $|\vec{v}(t)|$

$$
|\vec{v}(t)| = \omega\sqrt{a^2\sin^2(\omega t) + b^2\cos^2(\omega t)}
$$

For $a = 3$, $b = 2$, $\omega = 1$:

$$
|\vec{v}(t)| = \sqrt{9\sin^2 t + 4\cos^2 t}
$$

| $t$ | $|\vec{v}|$ | Note |
|:---:|:---:|:---|
| $0$ | $\sqrt{4} = 2$ | Minimum (at long axis tip) |
| $\pi/4$ | $\sqrt{6.5} \approx 2.55$ | Intermediate |
| $\pi/2$ | $\sqrt{9} = 3$ | Maximum (at short axis tip) |
| $\pi$ | $2$ | Minimum again |
| $3\pi/2$ | $3$ | Maximum again |

The graph oscillates between $b\omega = 2$ and $a\omega = 3$, completing
**two full cycles** per orbit (the speed peaks twice per revolution: once at
the top, once at the bottom of the ellipse).

### Graph of $|\vec{a}(t)|$

$$
|\vec{a}(t)| = \omega^2\sqrt{a^2\cos^2(\omega t) + b^2\sin^2(\omega t)}
$$

For $a = 3$, $b = 2$, $\omega = 1$:

$$
|\vec{a}(t)| = \sqrt{9\cos^2 t + 4\sin^2 t}
$$

| $t$ | $|\vec{a}|$ | Note |
|:---:|:---:|:---|
| $0$ | $\sqrt{9} = 3$ | Maximum (at long axis tip) |
| $\pi/2$ | $\sqrt{4} = 2$ | Minimum (at short axis tip) |
| $\pi$ | $3$ | Maximum again |
| $3\pi/2$ | $2$ | Minimum again |

Note: $|\vec{a}|$ is maximum exactly where $|\vec{v}|$ is minimum, and vice versa.

> **Explanation:**
> The trajectory equation $\frac{x^2}{a^2} + \frac{y^2}{b^2} = 1$ is the
> standard ellipse formula you may have seen in geometry. We got it by squaring
> both parametric equations and adding them — the $\sin^2 + \cos^2 = 1$ identity
> does the work. The speed graph oscillates smoothly between its minimum and
> maximum values twice per orbit. Interestingly, wherever the speed is highest,
> the acceleration magnitude is lowest, and vice versa — they are "out of phase"
> with each other. This is a distinctive feature of elliptical motion that does
> not appear in circular motion (where both are constant).

---

## Possible Questions and Answers

**Q1: What is the difference between this elliptical motion and circular motion
from Problem 4?**

A: Circular motion is a special case of elliptical motion where $a = b = R$.
When $a = b$, the ellipse becomes a circle, $|\vec{v}|$ becomes constant at $R\omega$,
and $|\vec{a}|$ becomes constant at $R\omega^2$. In elliptical motion with $a \neq b$,
the speed and acceleration magnitude both vary around the orbit — the body speeds
up and slows down. The result $\vec{a} = -\omega^2\vec{r}$ holds for both, but
its magnitude is only constant for a circle.

---

**Q2: How do you show that the trajectory is an ellipse algebraically?**

A: Start from $x = a\cos(\omega t)$ and $y = b\sin(\omega t)$. Divide:
$x/a = \cos(\omega t)$ and $y/b = \sin(\omega t)$. Square both equations:
$(x/a)^2 = \cos^2(\omega t)$ and $(y/b)^2 = \sin^2(\omega t)$. Add them:
$(x/a)^2 + (y/b)^2 = \cos^2(\omega t) + \sin^2(\omega t) = 1$.
This is the standard equation of an ellipse. The key step is recognising that
squaring and adding eliminates $t$ via the Pythagorean identity.

---

**Q3: At which points on the ellipse is the velocity vector parallel to the
$x$-axis, and at which is it parallel to the $y$-axis?**

A: The velocity is $\vec{v}(t) = (-a\omega\sin(\omega t),\ b\omega\cos(\omega t))$.
It is parallel to the $x$-axis when $v_y = 0$, i.e. $\cos(\omega t) = 0$,
which gives the points $(0, \pm b)$ — the tips of the vertical semi-axis.
It is parallel to the $y$-axis when $v_x = 0$, i.e. $\sin(\omega t) = 0$,
which gives the points $(\pm a, 0)$ — the tips of the horizontal semi-axis.
At all other points the velocity is diagonal.

---

**Q4: Does the acceleration ever point exactly toward the center of the ellipse
(like in circular motion)?**

A: The acceleration is $\vec{a}(t) = -\omega^2\vec{r}(t)$, so it always points
from the body toward the center (origin). In that sense it is always "centripetal."
However, unlike circular motion, the magnitude $|\vec{a}| = \omega^2|\vec{r}|$
varies because $|\vec{r}|$ is not constant on an ellipse. The direction is always
toward the center, but the strength of the pull changes depending on how far
from the center the body is at that moment.

---

**Q5: What is the period of the motion, and does it depend on $a$ and $b$?**

A: The body completes one full orbit when $\omega t = 2\pi$, so the period is:
$$
T = \frac{2\pi}{\omega}
$$
Remarkably, $T$ does **not** depend on $a$ or $b$ — only on $\omega$. A very
elongated ellipse and a nearly circular one with the same $\omega$ have
exactly the same period. This is analogous to the fact that the period of a
simple pendulum does not depend on the amplitude (for small oscillations).
The semi-axes $a$ and $b$ affect the shape, the speed, and the acceleration,
but not the time to complete one orbit.