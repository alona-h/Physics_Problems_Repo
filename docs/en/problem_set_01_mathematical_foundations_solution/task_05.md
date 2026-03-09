# Problem Set 1 – Problem 5: Trajectory Curvature and Normal Acceleration

---

## Overview

This problem investigates how an ellipse curves at different points, and how that curvature relates to acceleration. The central idea is that acceleration can be split into two parts:

- **Tangential acceleration** $\vec{a}_t$ — changes the object's *speed* (how fast it moves)
- **Normal acceleration** $\vec{a}_n$ — changes the object's *direction* (how sharply it turns)

The normal acceleration is directly linked to the curvature of the path: the sharper the turn, the larger the normal acceleration required.

> **Key formula connecting curvature and normal acceleration:**
> $$a_n = \frac{v^2}{R_c}$$
> where $v = |\vec{v}|$ is the speed and $R_c$ is the **radius of curvature** — the radius of the circle that best approximates the curve at that point. A small $R_c$ means a sharp bend; a large $R_c$ means a gentle curve.

**Given ellipse:**
$$x = a\cos t, \qquad y = b\sin t$$

---

## 5.1 – Velocity vector $\vec{v}(t)$ and acceleration vector $\vec{a}(t)$

Differentiating each component of $\vec{r}(t) = (a\cos t,\ b\sin t)$:

**Velocity** — first derivative:
$$\vec{v}(t) = \frac{d\vec{r}}{dt} = \left(\frac{d}{dt}(a\cos t),\ \frac{d}{dt}(b\sin t)\right)$$

$$= (-a\sin t,\ b\cos t)$$

$$\boxed{\vec{v}(t) = (-a\sin t,\ b\cos t)}$$

**Acceleration** — second derivative (differentiate $\vec{v}$):
$$\vec{a}(t) = \frac{d\vec{v}}{dt} = \left(\frac{d}{dt}(-a\sin t),\ \frac{d}{dt}(b\cos t)\right)$$

$$= (-a\cos t,\ -b\sin t)$$

$$\boxed{\vec{a}(t) = (-a\cos t,\ -b\sin t)}$$

Note that $\vec{a}(t) = -\vec{r}(t)$ — the acceleration always points toward the origin (centre of the ellipse).

> **Explanation:** The velocity is always tangent to the path — it tells you the direction of motion at each instant. The acceleration here always points back toward the centre of the ellipse. However, unlike a circle where this centripetal acceleration is purely responsible for changing direction, on an ellipse the acceleration is generally *not* perpendicular to the velocity — it has both a tangential component (changing speed) and a normal component (changing direction). We will separate these in the next steps.

---

## 5.2 – Unit tangent vector $\hat{T}(t)$

The **unit tangent vector** points in the direction of motion (same direction as $\vec{v}$) but has magnitude exactly 1:

$$\hat{T}(t) = \frac{\vec{v}(t)}{|\vec{v}(t)|}$$

**Step 1 — Compute $|\vec{v}(t)|$:**
$$|\vec{v}(t)| = \sqrt{(-a\sin t)^2 + (b\cos t)^2} = \sqrt{a^2\sin^2 t + b^2\cos^2 t}$$

Define $v(t) = |\vec{v}(t)| = \sqrt{a^2\sin^2 t + b^2\cos^2 t}$ for convenience.

**Step 2 — Write $\hat{T}(t)$:**

$$\boxed{\hat{T}(t) = \frac{(-a\sin t,\ b\cos t)}{\sqrt{a^2\sin^2 t + b^2\cos^2 t}}}$$

**Values at key points:**

- At $t = 0$: $\vec{v}(0) = (0, b)$, so $\hat{T}(0) = (0, 1)$ — pointing straight up
- At $t = \pi/2$: $\vec{v}(\pi/2) = (-a, 0)$, so $\hat{T}(\pi/2) = (-1, 0)$ — pointing left

> **Explanation:** The unit tangent vector is the "compass direction" of motion at each point. Dividing by the speed strips away information about how fast the object is moving, leaving only the direction. It is always tangent (touching) to the curve — never pointing into or away from it. We need it to decompose the acceleration into its two components in the next step.

---

## 5.3 – Decomposition of acceleration into tangential and normal components

Any acceleration vector can be split as:
$$\vec{a}(t) = \vec{a}_t(t) + \vec{a}_n(t)$$

where:
- $\vec{a}_t$ is **parallel** to $\hat{T}$ (along the direction of motion — changes speed)
- $\vec{a}_n$ is **perpendicular** to $\hat{T}$ (across the direction of motion — changes direction)

---

### Step 1 — Tangential acceleration $\vec{a}_t$

The tangential component is found by projecting $\vec{a}$ onto $\hat{T}$:

$$a_t = \vec{a} \cdot \hat{T} = \frac{\vec{a} \cdot \vec{v}}{|\vec{v}|}$$

**Compute $\vec{a} \cdot \vec{v}$:**
$$\vec{a} \cdot \vec{v} = (-a\cos t)(-a\sin t) + (-b\sin t)(b\cos t)$$

$$= a^2\sin t\cos t - b^2\sin t\cos t$$

$$= (a^2 - b^2)\sin t\cos t$$

Using the double-angle identity $\sin t \cos t = \frac{1}{2}\sin(2t)$:

$$\vec{a} \cdot \vec{v} = \frac{(a^2 - b^2)}{2}\sin(2t)$$

**Therefore the scalar tangential acceleration is:**
$$a_t = \frac{\vec{a} \cdot \vec{v}}{|\vec{v}|} = \frac{(a^2 - b^2)\sin t\cos t}{\sqrt{a^2\sin^2 t + b^2\cos^2 t}}$$

**And the tangential acceleration vector is:**
$$\vec{a}_t = a_t\,\hat{T} = \frac{(a^2 - b^2)\sin t\cos t}{a^2\sin^2 t + b^2\cos^2 t}\,(-a\sin t,\ b\cos t)$$

$$\boxed{\vec{a}_t(t) = \frac{(a^2-b^2)\sin t\cos t}{a^2\sin^2 t + b^2\cos^2 t}\,(-a\sin t,\ b\cos t)}$$

---

### Step 2 — Normal acceleration $\vec{a}_n$

The normal acceleration vector is whatever is left after subtracting the tangential part:
$$\vec{a}_n = \vec{a} - \vec{a}_t$$

**Scalar magnitude of normal acceleration:**

Using the identity $|\vec{a}|^2 = a_t^2 + a_n^2$ (Pythagoras — the two components are perpendicular), we get:

$$a_n = \sqrt{|\vec{a}|^2 - a_t^2}$$

**Compute $|\vec{a}|^2$:**
$$|\vec{a}|^2 = (-a\cos t)^2 + (-b\sin t)^2 = a^2\cos^2 t + b^2\sin^2 t$$

**Compute $a_t^2$:**
$$a_t^2 = \frac{(a^2-b^2)^2\sin^2 t\cos^2 t}{a^2\sin^2 t + b^2\cos^2 t}$$

**Therefore:**
$$a_n^2 = |\vec{a}|^2 - a_t^2 = (a^2\cos^2 t + b^2\sin^2 t) - \frac{(a^2-b^2)^2\sin^2 t\cos^2 t}{a^2\sin^2 t + b^2\cos^2 t}$$

Combining over a common denominator $v^2 = a^2\sin^2 t + b^2\cos^2 t$:

$$a_n^2 = \frac{(a^2\cos^2 t + b^2\sin^2 t)(a^2\sin^2 t + b^2\cos^2 t) - (a^2-b^2)^2\sin^2 t\cos^2 t}{a^2\sin^2 t + b^2\cos^2 t}$$

**Expanding the numerator:**

Let $A = a^2\cos^2 t + b^2\sin^2 t$ and $B = a^2\sin^2 t + b^2\cos^2 t$. Then:

$$AB = a^4\sin^2 t\cos^2 t + a^2 b^2\cos^4 t + a^2 b^2\sin^4 t + b^4\sin^2 t\cos^2 t$$

$$= (a^4 + b^4)\sin^2 t\cos^2 t + a^2 b^2(\sin^4 t + \cos^4 t)$$

Using $\sin^4 t + \cos^4 t = 1 - 2\sin^2 t\cos^2 t$:

$$AB = (a^4 + b^4)\sin^2 t\cos^2 t + a^2 b^2(1 - 2\sin^2 t\cos^2 t)$$

$$= a^2 b^2 + (a^4 + b^4 - 2a^2b^2)\sin^2 t\cos^2 t$$

$$= a^2 b^2 + (a^2 - b^2)^2\sin^2 t\cos^2 t$$

Subtracting $(a^2 - b^2)^2\sin^2 t\cos^2 t$:

$$AB - (a^2-b^2)^2\sin^2 t\cos^2 t = a^2 b^2$$

**Therefore:**

$$a_n^2 = \frac{a^2 b^2}{a^2\sin^2 t + b^2\cos^2 t}$$

$$\boxed{a_n(t) = \frac{ab}{\sqrt{a^2\sin^2 t + b^2\cos^2 t}} = \frac{ab}{|\vec{v}(t)|}}$$

> **Explanation:** The normal acceleration is the part of acceleration responsible for *bending* the path. It is always perpendicular to the direction of motion. The beautiful result $a_n = ab/|\vec{v}|$ tells us that the normal acceleration is large when the speed $|\vec{v}|$ is small — and small when the speed is large. This has an important geometric meaning: the object slows down in the parts of the ellipse where the path curves sharply (small $R_c$), and these are precisely the places where $|\vec{v}|$ is smaller.

---

## 5.4 – Radius of curvature at $t = 0$

Using the relation $a_n = v^2 / R_c$, solving for $R_c$:

$$R_c = \frac{v^2}{a_n} = \frac{|\vec{v}|^2}{a_n}$$

**At $t = 0$:**

Compute $|\vec{v}(0)|$:
$$\vec{v}(0) = (-a\sin 0,\ b\cos 0) = (0,\ b)$$
$$|\vec{v}(0)| = b$$

Compute $a_n(0)$:
$$a_n(0) = \frac{ab}{|\vec{v}(0)|} = \frac{ab}{b} = a$$

**Radius of curvature:**
$$R_c(t=0) = \frac{|\vec{v}(0)|^2}{a_n(0)} = \frac{b^2}{a}$$

$$\boxed{R_c(t=0) = \frac{b^2}{a}}$$

> **Explanation:** At $t = 0$ the object is at position $(a, 0)$ — the rightmost point of the ellipse, at the end of the **major semi-axis** $a$. The radius of curvature there is $b^2/a$. Since $b < a$ (assuming $a$ is the larger semi-axis), this gives $b^2/a < b < a$ — the curvature is *tightest* (smallest $R_c$) at the ends of the major axis. The ellipse bends most sharply at its widest points. This is the result we will compare with the circle case below.

---

## 5.5 – Comparison with a circle ($a = b$)

If $a = b = R$ (a circle), then:

**Radius of curvature everywhere:**
$$R_c = \frac{b^2}{a}\bigg|_{a=b=R} = \frac{R^2}{R} = R$$

This is constant — confirming that a circle has the **same curvature everywhere**, equal to its own radius. This is perfectly consistent: every point of a circle is the best approximated by a circle of the same radius $R$.

**Normal acceleration for a circle:**
$$a_n = \frac{ab}{|\vec{v}|}\bigg|_{a=b=R} = \frac{R^2}{\sqrt{R^2\sin^2 t + R^2\cos^2 t}} = \frac{R^2}{R} = R$$

This is also constant — consistent with uniform circular motion where the centripetal acceleration $a_n = \omega^2 R = R$ (for $\omega = 1$).

$$\boxed{\text{Circle: } R_c = R = \text{const}, \quad a_n = R = \text{const}}$$

> **Explanation:** The circle is the unique curve with *constant curvature*. Every other closed curve (like an ellipse with $a \neq b$) has varying curvature. The comparison shows that the ellipse "degenerates" smoothly into a circle as $a \to b$, and all the position-dependent variation in $R_c$ and $a_n$ disappears in that limit.

---

## Physical Interpretation

### Does greater curvature imply greater normal acceleration?

**Yes.** From $a_n = v^2/R_c$: if $R_c$ is small (sharp curvature), then $a_n$ is large (for the same speed). The tighter the bend, the more acceleration is needed to keep the object on the path. This is why racing cars need to slow down before sharp corners — at lower speed, the required centripetal force is smaller and the tyres can provide it without skidding.

---

### Where on the ellipse is the trajectory more curved: at the end of the major or minor semi-axis?

**At the end of the major semi-axis.** Let's compare:

- **End of major semi-axis** ($t = 0$, point $(a, 0)$): $R_c = b^2/a$
- **End of minor semi-axis** ($t = \pi/2$, point $(0, b)$):

At $t = \pi/2$:
$$|\vec{v}(\pi/2)| = \sqrt{a^2\sin^2(\pi/2) + b^2\cos^2(\pi/2)} = \sqrt{a^2} = a$$
$$a_n(\pi/2) = \frac{ab}{a} = b$$
$$R_c(t = \pi/2) = \frac{|\vec{v}|^2}{a_n} = \frac{a^2}{b}$$

Since $a > b$, we have $\frac{b^2}{a} < \frac{a^2}{b}$, i.e. $R_c$ is **smaller** at the end of the major axis — the curve is more tightly bent there.

$$\boxed{R_c\text{ at major axis end} = \frac{b^2}{a} < \frac{a^2}{b} = R_c\text{ at minor axis end}}$$

> **Explanation:** Imagine stretching a circle horizontally to make an ellipse. The ends that were pulled outward (the major axis ends) become the most sharply curved points — like the pointed ends of a football. The top and bottom (minor axis ends) become the flattest parts. So despite being the "widest" parts of the ellipse, the major axis ends are where the bending is most extreme.

---

### Why is normal acceleration the cause of change in direction of motion?

Normal acceleration acts **perpendicular** to the velocity vector. A force perpendicular to motion cannot change the magnitude of velocity (it does no work, since $\vec{F} \perp \vec{v}$ gives $\vec{F} \cdot \vec{v} = 0$). Instead, it continuously rotates the velocity vector — changing only its direction. This is why planets remain in orbit: gravity provides centripetal (normal) acceleration that continuously redirects their velocity into a curved path, without speeding them up or slowing them down (in the idealised circular case). The greater the normal acceleration, the more rapidly the direction of motion changes — i.e. the more sharply the path curves.

---

## Summary Table

| Quantity | General formula | At $t = 0$ | At $t = \pi/2$ |
|---|---|---|---|
| $\vec{v}(t)$ | $(-a\sin t,\ b\cos t)$ | $(0, b)$ | $(-a, 0)$ |
| $\vec{a}(t)$ | $(-a\cos t,\ -b\sin t)$ | $(-a, 0)$ | $(0, -b)$ |
| $|\vec{v}(t)|$ | $\sqrt{a^2\sin^2 t + b^2\cos^2 t}$ | $b$ | $a$ |
| $a_t$ (scalar) | $\frac{(a^2-b^2)\sin t\cos t}{|\vec{v}|}$ | $0$ | $0$ |
| $a_n$ (scalar) | $\frac{ab}{|\vec{v}|}$ | $a$ | $b$ |
| $R_c$ | $\frac{|\vec{v}|^3}{ab}$ | $\frac{b^2}{a}$ | $\frac{a^2}{b}$ |

> **Note:** At $t = 0$ and $t = \pi/2$, the tangential acceleration $a_t = 0$ — these are the points where the speed is momentarily at a maximum or minimum, so it is neither increasing nor decreasing. All the acceleration at these points is purely normal (centripetal).

---

## 5 Possible Questions & Answers

---

**Q1: Why is the tangential acceleration zero at $t = 0$ and $t = \pi/2$?**

**A:** The tangential acceleration is $a_t = (a^2 - b^2)\sin t \cos t / |\vec{v}|$. At $t = 0$: $\sin 0 = 0$, so $a_t = 0$. At $t = \pi/2$: $\cos(\pi/2) = 0$, so $a_t = 0$ again. Physically, these are the points where the speed $|\vec{v}|$ is at a local maximum or minimum — speed cannot be simultaneously increasing and at a maximum, so its rate of change (tangential acceleration) must be zero there, just as the derivative of any function is zero at its extrema. At $t = 0$ the speed equals $b$ (its minimum if $a > b$), and at $t = \pi/2$ the speed equals $a$ (its maximum).

---

**Q2: What is the physical meaning of the radius of curvature $R_c$?**

**A:** The radius of curvature $R_c$ at a point on a curve is the radius of the **osculating circle** — the unique circle that best approximates the curve at that point (same position, same tangent, same curvature). A small $R_c$ means the curve bends sharply (like the tip of an ellipse), while a large $R_c$ means the curve is nearly straight. For a circle, $R_c$ equals the circle's own radius at every point. The formula $a_n = v^2/R_c$ connects this purely geometric quantity to dynamics: it says that to follow a tightly curved path (small $R_c$) at speed $v$, you need a large centripetal (normal) acceleration.

---

**Q3: How does the decomposition $\vec{a} = \vec{a}_t + \vec{a}_n$ relate to Newton's second law?**

**A:** By Newton's second law, $\vec{F} = m\vec{a}$. If we decompose the acceleration, the total force is also decomposed: $\vec{F} = \vec{F}_t + \vec{F}_n$. The tangential force $\vec{F}_t = ma_t$ speeds the object up or slows it down. The normal force $\vec{F}_n = ma_n$ steers it — it keeps the object on its curved path without doing work. For example, a car's engine provides tangential force (acceleration/braking), while the tyres' sideways friction provides normal force (turning). The two effects are physically independent and can be analysed separately.

---

**Q4: What happens to the radius of curvature of the ellipse if $b \to 0$ (the ellipse becomes very flat)?**

**A:** If $b \to 0$, then at the end of the major axis: $R_c = b^2/a \to 0$ — the curvature becomes infinitely sharp (like the tip of a needle). At the end of the minor axis: $R_c = a^2/b \to \infty$ — the curve becomes nearly flat (almost a straight line). This makes geometric sense: as the ellipse flattens, its narrow tips become extremely pointed (high curvature) while the long sides become almost straight (nearly zero curvature). In the limit $b = 0$, the ellipse degenerates into a straight line segment of length $2a$, traversed back and forth.

---

**Q5: Show that the formula $R_c = |\vec{v}|^3 / (|\vec{v} \times \vec{a}|)$ gives the same result for the ellipse at $t = 0$.**

**A:** At $t = 0$: $\vec{v}(0) = (0, b)$ and $\vec{a}(0) = (-a, 0)$. The cross product in 2D gives a scalar (the $z$-component): $|\vec{v} \times \vec{a}| = |v_x a_y - v_y a_x| = |(0)(0) - (b)(-a)| = ab$. Then:
$$R_c = \frac{|\vec{v}|^3}{|\vec{v} \times \vec{a}|} = \frac{b^3}{ab} = \frac{b^2}{a}$$
This matches the result from Step 5.4, confirming both approaches are equivalent. This general formula is often used in practice because it avoids having to decompose the acceleration explicitly.