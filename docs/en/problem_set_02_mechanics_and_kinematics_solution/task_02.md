# Problem 2 – Projectile Motion

A body is launched with initial velocity $v_0$ at angle $\alpha$ above the horizontal,
moving under gravity alone (no air resistance).

---

## Question 2.1 – Derive the equations of motion in the horizontal and vertical directions

**Setup:**

At $t = 0$ the body is at the origin $(0, 0)$ with:
- Horizontal initial velocity: $v_{0x} = v_0 \cos\alpha$
- Vertical initial velocity: $v_{0y} = v_0 \sin\alpha$

The only force acting is gravity, pulling downward:
$$
a_x = 0, \qquad a_y = -g
$$

**Horizontal direction** (no acceleration):

Starting from $x(t) = x_0 + v_{0x}t + \frac{1}{2}a_x t^2$ with $x_0 = 0$, $a_x = 0$:

$$
\boxed{x(t) = v_0 \cos\alpha \cdot t}
$$

The horizontal velocity is constant throughout the flight:

$$
v_x(t) = v_0 \cos\alpha = \text{const}
$$

**Vertical direction** (constant downward acceleration $g$):

Starting from $y(t) = y_0 + v_{0y}t + \frac{1}{2}a_y t^2$ with $y_0 = 0$, $a_y = -g$:

$$
\boxed{y(t) = v_0 \sin\alpha \cdot t - \frac{1}{2}g t^2}
$$

The vertical velocity changes over time:

$$
v_y(t) = v_0 \sin\alpha - g t
$$

> **Explanation:**
> Projectile motion is actually two separate, independent motions happening at the same time. Horizontally, there is no force at all, so the body just keeps moving at the same speed forever — like sliding on a frictionless surface. Vertically, gravity pulls the body downward with acceleration $g \approx 9.81\ \text{m/s}^2$, exactly like a ball thrown straight up. The key insight is that these two directions do not affect each other. The horizontal motion does not care about gravity, and the vertical motion does not care about horizontal speed.

---

## Question 2.2 – Determine the time of flight

**Question:** How long is the body in the air?

**Solution:**

The body lands when it returns to $y = 0$ (ground level):

$$
y(t) = 0
$$

$$
v_0 \sin\alpha \cdot t - \frac{1}{2}g t^2 = 0
$$

Factor out $t$:

$$
t\!\left(v_0 \sin\alpha - \frac{1}{2}g t\right) = 0
$$

This gives two solutions:

$$
t = 0 \quad \text{(launch moment — trivial solution)}
$$

$$
v_0 \sin\alpha - \frac{1}{2}g t = 0 \implies t = \frac{2 v_0 \sin\alpha}{g}
$$

$$
\boxed{T = \frac{2 v_0 \sin\alpha}{g}}
$$

> **Explanation:**
> Setting $y = 0$ asks: "at what times is the body at ground level?" The answer is $t = 0$ (when it was launched) and $t = T$ (when it lands). The second solution is the one we care about. Notice that the time of flight depends only on the vertical component of the initial velocity ($v_0 \sin\alpha$) and on gravity $g$. The horizontal speed plays no role in how long the body stays airborne — a bullet fired horizontally and a ball dropped from the same height both hit the ground at the same time.

---

## Question 2.3 – Determine the maximum height

**Question:** What is the highest point the body reaches?

**Solution:**

The body is at maximum height when the vertical velocity equals zero (it stops going up before it starts coming down):

$$
v_y(t) = 0
$$

$$
v_0 \sin\alpha - g t = 0
$$

$$
t_{\text{top}} = \frac{v_0 \sin\alpha}{g}
$$

Note: this is exactly **half** the total flight time $T$, which makes sense by symmetry.

Now substitute $t_{\text{top}}$ into $y(t)$:

$$
H = y(t_{\text{top}}) = v_0 \sin\alpha \cdot \frac{v_0 \sin\alpha}{g} - \frac{1}{2}g\left(\frac{v_0 \sin\alpha}{g}\right)^2
$$

$$
H = \frac{v_0^2 \sin^2\alpha}{g} - \frac{1}{2}g \cdot \frac{v_0^2 \sin^2\alpha}{g^2}
$$

$$
H = \frac{v_0^2 \sin^2\alpha}{g} - \frac{v_0^2 \sin^2\alpha}{2g}
$$

$$
H = \frac{v_0^2 \sin^2\alpha}{g}\left(1 - \frac{1}{2}\right)
$$

$$
\boxed{H = \frac{v_0^2 \sin^2\alpha}{2g}}
$$

> **Explanation:**
> At the very top of the trajectory, the body is neither going up nor going down — the vertical velocity is zero for just an instant. That moment in time is $t_{\text{top}}$. Plugging it back into the height formula gives the maximum height $H$. You can see that $H$ grows with $v_0^2$ (launch speed matters a lot) and with $\sin^2\alpha$ (steeper angles give greater height, up to $90°$ which is straight up). Horizontal speed contributes nothing to how high the body goes.

---

## Question 2.4 – Determine the range

**Question:** How far from the launch point does the body land?

**Solution:**

The range is the horizontal distance at the moment of landing $t = T$:

$$
R = x(T) = v_0 \cos\alpha \cdot T
$$

Substitute $T = \dfrac{2v_0 \sin\alpha}{g}$:

$$
R = v_0 \cos\alpha \cdot \frac{2 v_0 \sin\alpha}{g}
$$

$$
R = \frac{2 v_0^2 \sin\alpha \cos\alpha}{g}
$$

Using the double-angle identity $2\sin\alpha\cos\alpha = \sin(2\alpha)$:

$$
\boxed{R = \frac{v_0^2 \sin(2\alpha)}{g}}
$$

> **Explanation:**
> The range is simply: "how fast am I going horizontally" times "how long am I in the air". The neat simplification using $\sin(2\alpha)$ shows that the range depends on the angle through a single sine function of the doubled angle. This will be very useful in the next question.

---

## Question 2.5 – For what angle is the range maximum?

**Solution:**

From the range formula:

$$
R = \frac{v_0^2 \sin(2\alpha)}{g}
$$

The range is maximum when $\sin(2\alpha)$ is maximum. The sine function reaches its maximum value of $1$ when its argument equals $90°$:

$$
\sin(2\alpha) = 1
$$

$$
2\alpha = 90°
$$

$$
\boxed{\alpha = 45°}
$$

The maximum range is:

$$
R_{\max} = \frac{v_0^2}{g}
$$

**Verification — symmetry of the range:**

Note that $\sin(2\alpha) = \sin(180° - 2\alpha) = \sin(2(90° - \alpha))$, which means:

$$
R(\alpha) = R(90° - \alpha)
$$

For example, $\alpha = 30°$ and $\alpha = 60°$ give exactly the same range. The two angles are always symmetric around $45°$.

> **Explanation:**
> Since $R \propto \sin(2\alpha)$, and the sine function peaks at $90°$, the range is largest when $2\alpha = 90°$, i.e. $\alpha = 45°$. This is a famous result in physics: a $45°$ launch angle gives the maximum horizontal distance (on flat ground, with no air resistance). The symmetry result is also intuitive — a very flat shot ($30°$) and a very steep shot ($60°$) travel the same horizontal distance, just with very different shapes of trajectory. The flat one is fast but low; the steep one is slow horizontally but spends more time in the air.

---

## Question 2.6 – Animation of the trajectory for different $\alpha$

Below is a description of what the animation or set of plots shows.

**Trajectory equation (eliminating $t$):**

From $x = v_0\cos\alpha \cdot t$ we get $t = \dfrac{x}{v_0 \cos\alpha}$.

Substitute into $y(t)$:

$$
y = v_0\sin\alpha \cdot \frac{x}{v_0\cos\alpha} - \frac{1}{2}g\left(\frac{x}{v_0\cos\alpha}\right)^2
$$

$$
\boxed{y(x) = x\tan\alpha - \frac{g}{2v_0^2\cos^2\alpha}\,x^2}
$$

This is a **downward-opening parabola** in $x$.

**Summary table for $v_0 = 10\ \text{m/s}$, $g = 9.81\ \text{m/s}^2$:**

| $\alpha$ | $T\ (\text{s})$ | $H\ (\text{m})$ | $R\ (\text{m})$ |
|:---:|:---:|:---:|:---:|
| $15°$ | 0.53 | 0.33 | 5.10 |
| $30°$ | 1.02 | 1.27 | 8.83 |
| $45°$ | 1.44 | 2.55 | 10.19 |
| $60°$ | 1.77 | 3.82 | 8.83 |
| $75°$ | 1.97 | 4.70 | 5.10 |
| $90°$ | 2.04 | 5.10 | 0 |

**Key observations visible from the plots:**
- $\alpha = 45°$ gives the longest range
- $30°$ and $60°$ produce identical ranges (symmetry around $45°$)
- Higher angles produce taller but shorter trajectories
- $\alpha = 90°$ (straight up) gives zero range and maximum height

> **Explanation:**
> The trajectory formula $y(x)$ shows that the path is a parabola — a smooth, symmetric arch. For small angles the path is flat and wide; for large angles it is tall and narrow. The animation (or set of overlaid curves) makes it visually clear that $45°$ hits the sweet spot: it balances "going fast horizontally" with "staying in the air long enough." The table also confirms that $15°$ and $75°$ give the same range, as do $30°$ and $60°$.

---

## Possible Questions and Answers

**Q1: Why is the horizontal acceleration zero in projectile motion?**

A: Because the only force acting on the body is gravity, which acts purely in the vertical (downward) direction. By Newton's second law, $a = F/m$, so if there is no horizontal force, there is no horizontal acceleration. The horizontal velocity therefore stays constant throughout the entire flight.

---

**Q2: At what point in the trajectory is the speed (magnitude of velocity) minimum?**

A: At the highest point of the trajectory. At that moment the vertical component of velocity $v_y = 0$, so the total speed is $|\vec{v}| = \sqrt{v_x^2 + v_y^2} = |v_x| = v_0\cos\alpha$, which is the smallest value it ever takes. The horizontal component $v_x$ never changes, so the minimum speed equals $v_0\cos\alpha$.

---

**Q3: How does doubling the initial speed $v_0$ affect the range?**

A: The range is $R = \dfrac{v_0^2\sin(2\alpha)}{g}$, so it depends on $v_0^2$. Doubling $v_0$ increases the range by a factor of $2^2 = 4$. This quadratic dependence means that small increases in launch speed produce large increases in range.

---

**Q4: Does the time of flight depend on the initial horizontal velocity?**

A: No. The time of flight is $T = \dfrac{2v_0\sin\alpha}{g}$, which depends only on the vertical component of the initial velocity $v_{0y} = v_0\sin\alpha$ and on gravity. Two projectiles launched at the same angle and speed but in different gravitational fields would have different flight times, but changing only $\cos\alpha$ (the horizontal component) does not affect $T$.

---

**Q5: What assumption does the formula $R = \dfrac{v_0^2\sin(2\alpha)}{g}$ rely on, and when does it break down?**

A: The formula assumes: (1) the launch and landing heights are equal (flat ground), (2) there is no air resistance, and (3) $g$ is constant (valid near Earth's surface). It breaks down for very long ranges (where Earth's curvature matters), for objects with significant air drag (e.g. a feather or a bullet at high speed), and when the landing point is at a different height than the launch point (e.g. throwing off a cliff), in which case $T$ changes and a modified formula is needed.