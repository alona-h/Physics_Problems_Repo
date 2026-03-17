# Problem 6 – Cycloid: Trajectory of a Point on a Rolling Circle

A circle of radius $R$ rolls without slipping along the $x$-axis.
A point on the rim traces a cycloid:

$$
x(t) = R(\omega t - \sin(\omega t)), \qquad y(t) = R(1 - \cos(\omega t))
$$

---

## Question 6.1 – Determine the velocity vector $\vec{v}(t)$ and acceleration $\vec{a}(t)$

### Velocity vector $\vec{v}(t)$

**Question:** Find $\vec{v}(t)$ by differentiating each component of the position.

**Solution:**

Differentiate $x(t) = R(\omega t - \sin(\omega t))$ with respect to $t$:

$$
v_x(t) = \frac{dx}{dt} = \frac{d}{dt}\bigl[R(\omega t - \sin(\omega t))\bigr]
$$

Differentiate term by term (chain rule on $\sin(\omega t)$):

$$
\frac{d}{dt}(\omega t) = \omega
$$

$$
\frac{d}{dt}(\sin(\omega t)) = \omega\cos(\omega t)
$$

$$
v_x(t) = R(\omega - \omega\cos(\omega t)) = R\omega(1 - \cos(\omega t))
$$

Differentiate $y(t) = R(1 - \cos(\omega t))$ with respect to $t$:

$$
v_y(t) = \frac{dy}{dt} = \frac{d}{dt}\bigl[R(1 - \cos(\omega t))\bigr]
$$

$$
\frac{d}{dt}(1) = 0
$$

$$
\frac{d}{dt}(-\cos(\omega t)) = \omega\sin(\omega t)
$$

$$
v_y(t) = R\omega\sin(\omega t)
$$

$$
\boxed{\vec{v}(t) = \bigl(R\omega(1 - \cos(\omega t)),\ R\omega\sin(\omega t)\bigr)}
$$

### Acceleration vector $\vec{a}(t)$

**Question:** Find $\vec{a}(t)$ by differentiating $\vec{v}(t)$.

**Solution:**

Differentiate $v_x(t) = R\omega(1 - \cos(\omega t))$:

$$
a_x(t) = \frac{dv_x}{dt} = \frac{d}{dt}\bigl[R\omega(1 - \cos(\omega t))\bigr]
$$

$$
\frac{d}{dt}(1) = 0, \qquad \frac{d}{dt}(-\cos(\omega t)) = \omega\sin(\omega t)
$$

$$
a_x(t) = R\omega \cdot \omega\sin(\omega t) = R\omega^2\sin(\omega t)
$$

Differentiate $v_y(t) = R\omega\sin(\omega t)$:

$$
a_y(t) = \frac{dv_y}{dt} = \frac{d}{dt}\bigl[R\omega\sin(\omega t)\bigr]
$$

$$
\frac{d}{dt}(\sin(\omega t)) = \omega\cos(\omega t)
$$

$$
a_y(t) = R\omega \cdot \omega\cos(\omega t) = R\omega^2\cos(\omega t)
$$

$$
\boxed{\vec{a}(t) = \bigl(R\omega^2\sin(\omega t),\ R\omega^2\cos(\omega t)\bigr)}
$$

> **Explanation:**
> We differentiate the position components one at a time, using the chain rule
> for $\sin(\omega t)$ and $\cos(\omega t)$ — each differentiation brings down
> a factor of $\omega$. The velocity $\vec{v}(t)$ combines the forward rolling
> motion (the constant $R\omega$ part in $v_x$) with the rotational motion
> (the $\sin$ and $\cos$ parts). The acceleration $\vec{a}(t)$ comes purely
> from the rotation — the constant rolling speed contributes zero acceleration,
> just like in Problem 4. Notice that unlike circular motion, neither component
> of $\vec{v}$ or $\vec{a}$ has a minus sign in front — the structure is
> different because the circle is rolling forward, not spinning in place.

---

## Question 6.2 – Calculate $|\vec{v}(t)|$ and find when the point stops

### Magnitude of velocity $|\vec{v}(t)|$

**Question:** Find the speed at every moment and identify when it equals zero.

**Solution:**

$$
|\vec{v}(t)| = \sqrt{v_x^2 + v_y^2}
= \sqrt{\bigl[R\omega(1-\cos(\omega t))\bigr]^2 + \bigl[R\omega\sin(\omega t)\bigr]^2}
$$

Factor out $(R\omega)^2$:

$$
= R\omega\sqrt{(1-\cos(\omega t))^2 + \sin^2(\omega t)}
$$

Expand $(1 - \cos(\omega t))^2$:

$$
(1-\cos(\omega t))^2 = 1 - 2\cos(\omega t) + \cos^2(\omega t)
$$

So the expression under the root becomes:

$$
1 - 2\cos(\omega t) + \cos^2(\omega t) + \sin^2(\omega t)
$$

Use $\sin^2(\omega t) + \cos^2(\omega t) = 1$:

$$
= 1 - 2\cos(\omega t) + 1 = 2 - 2\cos(\omega t) = 2(1 - \cos(\omega t))
$$

Now use the half-angle identity:

$$
1 - \cos(\omega t) = 2\sin^2\!\left(\frac{\omega t}{2}\right)
$$

Therefore:

$$
|\vec{v}(t)| = R\omega\sqrt{2 \cdot 2\sin^2\!\left(\frac{\omega t}{2}\right)}
= R\omega\sqrt{4\sin^2\!\left(\frac{\omega t}{2}\right)}
= R\omega \cdot 2\left|\sin\!\left(\frac{\omega t}{2}\right)\right|
$$

$$
\boxed{|\vec{v}(t)| = 2R\omega\left|\sin\!\left(\frac{\omega t}{2}\right)\right|}
$$

### When does the point stop?

The point stops when $|\vec{v}(t)| = 0$:

$$
2R\omega\left|\sin\!\left(\frac{\omega t}{2}\right)\right| = 0
$$

$$
\sin\!\left(\frac{\omega t}{2}\right) = 0
$$

$$
\frac{\omega t}{2} = n\pi, \quad n = 0, 1, 2, \ldots
$$

$$
\boxed{t_n = \frac{2\pi n}{\omega}, \quad n = 0, 1, 2, \ldots}
$$

These are exactly the moments when the rolling circle has completed $n$ full
revolutions — the point on the rim touches the ground again.

**Position at stopping moments:**

$$
x(t_n) = R(\omega \cdot \tfrac{2\pi n}{\omega} - \sin(2\pi n)) = R(2\pi n - 0) = 2\pi R n
$$

$$
y(t_n) = R(1 - \cos(2\pi n)) = R(1 - 1) = 0
$$

So the point stops at positions $(0,\ 0)$, $(2\pi R,\ 0)$, $(4\pi R,\ 0)$, $\ldots$ —
equally spaced points on the $x$-axis, separated by one full circumference $2\pi R$.

> **Explanation:**
> The half-angle identity $1 - \cos\theta = 2\sin^2(\theta/2)$ is the key algebraic
> trick here — it turns a messy expression into a clean square that can be
> square-rooted. The result $|\vec{v}| = 2R\omega|\sin(\omega t / 2)|$ shows
> that the speed oscillates smoothly between $0$ and $2R\omega$. The point stops
> every time it touches the ground, which makes perfect physical sense: the
> bottom of a rolling wheel has zero velocity relative to the ground (this is
> the no-slip condition). Between touches, it sweeps up into an arch and reaches
> maximum speed at the very top.

---

## Question 6.3 – Maximum values of $|\vec{v}|$ and $|\vec{a}|$

### Maximum speed $|\vec{v}|_{\max}$

**Question:** What is the highest speed the point reaches, and where does this occur?

**Solution:**

From the result above:

$$
|\vec{v}(t)| = 2R\omega\left|\sin\!\left(\frac{\omega t}{2}\right)\right|
$$

This is maximum when $\left|\sin\!\left(\dfrac{\omega t}{2}\right)\right| = 1$:

$$
\frac{\omega t}{2} = \frac{\pi}{2} + n\pi \implies \omega t = \pi + 2\pi n
$$

$$
t^* = \frac{\pi(2n+1)}{\omega}, \quad n = 0, 1, 2, \ldots
$$

$$
\boxed{|\vec{v}|_{\max} = 2R\omega}
$$

**Position at maximum speed:**

$$
x(t^*) = R(\pi(2n+1) - \sin(\pi(2n+1))) = R(\pi(2n+1) - 0) = R\pi(2n+1)
$$

$$
y(t^*) = R(1 - \cos(\pi(2n+1))) = R(1 - (-1)) = 2R
$$

The point is at its **maximum height** $y = 2R$ — the very top of the arch.
At the top, the velocity is purely horizontal:

$$
\vec{v}(t^*) = \bigl(R\omega(1-(-1)),\ R\omega \cdot 0\bigr) = (2R\omega,\ 0)
$$

### Maximum acceleration $|\vec{a}|_{\max}$

**Question:** What is the highest acceleration magnitude, and where does it occur?

**Solution:**

Calculate $|\vec{a}(t)|$:

$$
|\vec{a}(t)| = \sqrt{a_x^2 + a_y^2}
= \sqrt{(R\omega^2\sin(\omega t))^2 + (R\omega^2\cos(\omega t))^2}
$$

$$
= R\omega^2\sqrt{\sin^2(\omega t) + \cos^2(\omega t)}
$$

$$
= R\omega^2\sqrt{1}
$$

$$
\boxed{|\vec{a}(t)| = R\omega^2 = \text{const}}
$$

The acceleration magnitude is **constant** for all $t$!

$$
\boxed{|\vec{a}|_{\max} = |\vec{a}|_{\min} = R\omega^2}
$$

> **Explanation:**
> The maximum speed of $2R\omega$ occurs at the top of each arch ($y = 2R$).
> This is intuitive: at the top of the wheel, the rotational motion and the
> forward rolling motion both point in the same direction (both are to the right
> at the top), so they add together to give double the rolling speed $R\omega$.
> At the bottom (contact point), the rotational motion points backward and
> exactly cancels the forward rolling, giving zero speed.
>
> The constant acceleration magnitude $R\omega^2$ is a beautiful and surprising
> result. Even though the direction of $\vec{a}$ changes continuously, its
> length never changes. This is because the acceleration comes entirely from
> the circular rotation of the point around the moving center of the wheel —
> and circular motion always has constant centripetal acceleration magnitude
> $R\omega^2$ (exactly as we found in Problem 4).

---

## Question 6.4 – HTML Animation Description

**Question:** What should the animation show?

**The animation consists of the following elements:**

**1. Rolling circle:**
- A circle of radius $R$ whose center moves along the line $y = R$ at constant speed
- Center position at time $t$: $\bigl(R\omega t,\ R\bigr)$
- The circle rotates clockwise as it rolls to the right

**2. The point on the rim:**
- Highlighted dot on the circumference of the rolling circle
- Its position is given by:
$$
\bigl(R(\omega t - \sin(\omega t)),\ R(1 - \cos(\omega t))\bigr)
$$

**3. The cycloid trace:**
- The path drawn by the point as the animation progresses
- Forms a sequence of arches, each of width $2\pi R$ and height $2R$

**4. Optional — velocity and acceleration vectors:**
- Velocity arrow at the current point:
$$
\vec{v}(t) = \bigl(R\omega(1-\cos(\omega t)),\ R\omega\sin(\omega t)\bigr)
$$
- Acceleration arrow at the current point (always pointing toward the center of the rolling circle):
$$
\vec{a}(t) = \bigl(R\omega^2\sin(\omega t),\ R\omega^2\cos(\omega t)\bigr)
$$

**Key moments visible in the animation:**

| Moment | Event | $y$ | $|\vec{v}|$ |
|:---|:---:|:---:|:---:|
| Point touches ground | Cusp, stop | $0$ | $0$ |
| Point at top of arch | Maximum speed | $2R$ | $2R\omega$ |
| All other moments | Smooth arch | $0$ to $2R$ | $0$ to $2R\omega$ |

> **Explanation:**
> The animation brings together all the mathematical results. You can literally
> watch the speed arrow shrink to zero each time the point touches the ground
> (the cusp) and grow to its maximum $2R\omega$ at the top of each arch.
> The acceleration arrow always points toward the center of the rolling circle —
> rotating as the circle rolls, but never changing its length. This is the
> clearest way to see that the cycloid is composed of pure rolling (forward
> translation) plus pure rotation (circular motion around the moving center).

---

## Question 6.5 – Compare the cycloid with circular motion in the frame attached to the circle

**Question:** What does the motion look like from the perspective of an observer
riding on the center of the rolling circle?

**Solution:**

**In the lab frame (ground):**

Position of the point:
$$
\vec{r}_{\text{lab}}(t) = \bigl(R(\omega t - \sin(\omega t)),\ R(1-\cos(\omega t))\bigr)
$$

Position of the center of the rolling circle:
$$
\vec{r}_{\text{center}}(t) = (R\omega t,\ R)
$$

**In the frame attached to the circle's center:**

The position of the point **relative to the center** is:

$$
\vec{r}_{\text{rel}}(t) = \vec{r}_{\text{lab}}(t) - \vec{r}_{\text{center}}(t)
$$

$$
x_{\text{rel}} = R(\omega t - \sin(\omega t)) - R\omega t = -R\sin(\omega t)
$$

$$
y_{\text{rel}} = R(1 - \cos(\omega t)) - R = -R\cos(\omega t)
$$

$$
\boxed{\vec{r}_{\text{rel}}(t) = \bigl(-R\sin(\omega t),\ -R\cos(\omega t)\bigr)}
$$

**This is circular motion!**

Check the magnitude:

$$
|\vec{r}_{\text{rel}}| = \sqrt{R^2\sin^2(\omega t) + R^2\cos^2(\omega t)} = R = \text{const}
$$

The point moves in a **circle of radius $R$** around the center of the rolling circle,
with angular velocity $\omega$.

**Comparison table:**

| Property | Lab frame (cycloid) | Circle's frame (circular) |
|:---|:---:|:---:|
| Path shape | Arched cycloid | Circle of radius $R$ |
| Speed | $2R\omega\|\sin(\omega t/2)\|$ (variable) | $R\omega$ (constant) |
| Speed at ground contact | $0$ (stops!) | $R\omega$ (never stops) |
| Acceleration magnitude | $R\omega^2$ (constant) | $R\omega^2$ (constant) |
| Acceleration direction | Toward rolling center (rotating) | Centripetal (toward center) |

> **Explanation:**
> This comparison is one of the most elegant results in kinematics. The rolling
> motion in the lab frame — which traces the complicated arch-shaped cycloid —
> is secretly just **simple circular motion** viewed from a moving platform.
> An ant sitting at the center of the wheel would see the rim point going around
> in a perfect circle. A person standing on the ground sees the same point
> tracing arches with stops and speed changes. Neither view is "more correct" —
> they are the same motion described in two different reference frames.
> This decomposition (translation of center + rotation around center) is a
> fundamental idea in mechanics and is used everywhere from gear design to
> planetary motion.

---

## Possible Questions and Answers

**Q1: What does "rolling without slipping" mean mathematically, and how does it
appear in the cycloid equations?**

A: Rolling without slipping means the distance the circle has rolled along the
ground equals the arc length swept on the rim. If the circle has rotated by angle
$\theta = \omega t$, the center has moved forward by $R\theta = R\omega t$ along
the $x$-axis. This is why the $x$-component of the center is $R\omega t$ and the
$x$-component of the cycloid is $R\omega t - R\sin(\omega t)$: the first term is
the forward translation and the second is the rotational offset. If the wheel
slipped, these two would not be coupled and the formula would be different.

---

**Q2: Why does the point on the rim come to a complete stop at the ground, but
only instantaneously?**

A: At the contact point the rim velocity due to rotation ($-R\omega$ backward)
exactly cancels the forward rolling velocity ($+R\omega$), giving zero net velocity.
This cancellation is exact only at that single instant — immediately before and
after, the rotational and translational velocities do not perfectly cancel and the
speed is non-zero. Mathematically, $|\vec{v}| = 2R\omega|\sin(\omega t/2)|$, which
touches zero but does not stay there. The point does not "rest" on the ground; it
instantaneously stops and then immediately starts moving again.

---

**Q3: The acceleration magnitude $|\vec{a}| = R\omega^2$ is constant. What is the
physical reason for this?**

A: The acceleration of the rim point in the lab frame comes entirely from its
circular motion around the moving center of the wheel. Translational motion at
constant velocity (the center rolling at constant speed $R\omega$) contributes
zero acceleration. Circular motion of radius $R$ at angular velocity $\omega$
always produces centripetal acceleration of magnitude $R\omega^2$ (as derived
in Problem 4), regardless of where the point is in its cycle. Since only the
rotational part contributes to acceleration, and that part is always the same
centripetal magnitude, $|\vec{a}|$ is constant.

---

**Q4: What is the direction of the acceleration vector at the moment the point
touches the ground?**

A: At the ground contact ($\omega t = 2\pi n$):

$$
\vec{a}(t_n) = \bigl(R\omega^2\sin(2\pi n),\ R\omega^2\cos(2\pi n)\bigr)
= (0,\ R\omega^2)
$$

The acceleration points **straight upward** ($+y$ direction). This makes physical
sense: at the contact point, the center of the circle is directly above, so the
centripetal acceleration (directed from rim point toward center) points straight up.
Even though the point has zero velocity at this moment, it has maximum acceleration
directed upward — it is about to be "flung" back up into the next arch.

---

**Q5: How does the shape of the cycloid arch change if $R$ or $\omega$ changes?**

A: The shape of each arch (its proportions) depends only on $R$, not on $\omega$.
Each arch always has width $2\pi R$ and height $2R$, giving a fixed ratio of
height to width of $1/\pi \approx 0.318$, regardless of how fast the wheel spins.
Increasing $R$ scales the entire arch up proportionally. Changing $\omega$ only
affects the speed at which the point traverses the same arch: a larger $\omega$
means the point moves faster and the arc is traced more quickly, but the geometric
path is identical. The period of one arch is $T = 2\pi/\omega$, which decreases
as $\omega$ increases.