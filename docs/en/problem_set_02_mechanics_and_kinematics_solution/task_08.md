# Problem 8 – Relative Motion

Given:
- Velocity of body A: $\vec{v}_A = (3,\ 1)$ (in m/s)
- Velocity of body B: $\vec{v}_B = (1,\ -2)$ (in m/s)
- Both bodies start at the origin at $t = 0$:
  $\vec{r}_A(0) = (0,\ 0)$, $\vec{r}_B(0) = (0,\ 0)$

---

## Question 8.1 – Determine the relative velocity $\vec{v}_{A/B}$

**Question:** What is the velocity of body A as seen by an observer
riding on body B?

**Solution:**

The relative velocity of A with respect to B is defined as:

$$
\vec{v}_{A/B} = \vec{v}_A - \vec{v}_B
$$

Substitute the given values:

$$
\vec{v}_{A/B} = (3,\ 1) - (1,\ -2)
$$

Subtract component by component:

$$
x\text{-component: } 3 - 1 = 2
$$

$$
y\text{-component: } 1 - (-2) = 1 + 2 = 3
$$

$$
\boxed{\vec{v}_{A/B} = (2,\ 3)\ \text{m/s}}
$$

**Magnitude of relative velocity:**

$$
|\vec{v}_{A/B}| = \sqrt{2^2 + 3^2} = \sqrt{4 + 9} = \sqrt{13} \approx 3.61\ \text{m/s}
$$

**Also compute $\vec{v}_{B/A}$ (velocity of B as seen from A):**

$$
\vec{v}_{B/A} = \vec{v}_B - \vec{v}_A = (1,\ -2) - (3,\ 1) = (-2,\ -3)\ \text{m/s}
$$

Note: $\vec{v}_{B/A} = -\vec{v}_{A/B}$ — they are equal and opposite, as expected.

> **Explanation:**
> Relative velocity answers the question: "How fast and in what direction does
> A appear to move when you are sitting on B?" To find it, you subtract B's
> velocity from A's velocity. Think of it like this: if two cars are both
> driving east at $100$ km/h, neither appears to move relative to the other —
> the relative velocity is zero. If A drives east at $3$ m/s and B drives east
> at $1$ m/s, then from B's perspective A is moving east at only $2$ m/s.
> The subtraction automatically accounts for both components simultaneously.
> The minus sign when computing the $y$-component ($1 - (-2) = 3$) is important
> — B is moving downward ($v_{By} = -2$), so from B's point of view, A appears
> to be moving upward even faster.

---

## Question 8.2 – Determine the direction of relative motion

**Question:** What angle does the relative velocity $\vec{v}_{A/B} = (2,\ 3)$
make with the positive $x$-axis?

**Solution:**

The direction of a vector $(v_x,\ v_y)$ is given by the angle:

$$
\theta = \arctan\!\left(\frac{v_y}{v_x}\right)
$$

Substitute $v_x = 2$, $v_y = 3$:

$$
\theta = \arctan\!\left(\frac{3}{2}\right) = \arctan(1.5)
$$

$$
\boxed{\theta \approx 56.3°\ \text{above the positive } x\text{-axis}}
$$

**Verification using components:**

The vector $(2, 3)$ points into the **first quadrant** (both components positive),
so the angle must be between $0°$ and $90°$. Our result of $56.3°$ is consistent.

**Unit vector (direction only):**

$$
\hat{v}_{A/B} = \frac{\vec{v}_{A/B}}{|\vec{v}_{A/B}|} = \frac{(2,\ 3)}{\sqrt{13}}
= \left(\frac{2}{\sqrt{13}},\ \frac{3}{\sqrt{13}}\right) \approx (0.555,\ 0.832)
$$

> **Explanation:**
> The direction of motion is found using the arctangent of the ratio of the
> vertical to horizontal component — this is basic trigonometry. Imagine drawing
> the vector $(2, 3)$ on a graph: go $2$ units to the right and $3$ units up.
> The angle this arrow makes with the horizontal is $\arctan(3/2) \approx 56.3°$.
> This means that from B's perspective, A is moving at roughly $56°$ above
> horizontal — more upward than sideways. The unit vector tells us the pure
> direction (stripped of magnitude): it has length exactly $1$ and points in
> the same direction as $\vec{v}_{A/B}$.

---

## Question 8.3 – Visualize motion in three reference frames

### Setting up the position equations

Since both bodies move with **constant velocity** starting from the origin,
their positions at time $t$ are:

$$
\vec{r}_A(t) = \vec{v}_A \cdot t = (3t,\ t)
$$

$$
\vec{r}_B(t) = \vec{v}_B \cdot t = (t,\ -2t)
$$

---

### Frame 1 – Reference frame attached to the origin (lab frame)

**Question:** What do the trajectories of A and B look like to a stationary
observer at the origin?

**Solution:**

Both bodies move in straight lines from the origin with constant velocities:

**Body A:** moves along the line defined by direction $(3, 1)$

$$
\text{Trajectory: } y = \frac{1}{3}x \quad \text{(slope } = \frac{v_{Ay}}{v_{Ax}} = \frac{1}{3}\text{)}
$$

**Body B:** moves along the line defined by direction $(1, -2)$

$$
\text{Trajectory: } y = -2x \quad \text{(slope } = \frac{v_{By}}{v_{Bx}} = \frac{-2}{1} = -2\text{)}
$$

**Position table (lab frame):**

| $t\ (\text{s})$ | $\vec{r}_A = (3t,\ t)$ | $\vec{r}_B = (t,\ -2t)$ |
|:---:|:---:|:---:|
| $0$ | $(0,\ 0)$ | $(0,\ 0)$ |
| $1$ | $(3,\ 1)$ | $(1,\ -2)$ |
| $2$ | $(6,\ 2)$ | $(2,\ -4)$ |
| $3$ | $(9,\ 3)$ | $(3,\ -6)$ |

The two bodies start together and immediately diverge — A moves up and to the
right, B moves down and to the right.

**Angle each trajectory makes with the $x$-axis:**

$$
\theta_A = \arctan\!\left(\frac{1}{3}\right) \approx 18.4°\ \text{above horizontal}
$$

$$
\theta_B = \arctan\!\left(\frac{-2}{1}\right) \approx -63.4°\ \text{below horizontal}
$$

> **Explanation:**
> In the lab frame (standing still at the origin watching both bodies), each
> body simply moves in a straight line because both have constant velocities.
> A drifts gently upward to the right at $18.4°$. B heads steeply downward to
> the right at $63.4°$ below horizontal. The two lines diverge from the origin
> like an opening pair of scissors. This is the simplest view — no tricks, just
> two arrows moving in fixed directions.

---

### Frame 2 – Reference frame attached to body A

**Question:** What does the motion of B look like to an observer riding on A?

**Solution:**

In A's frame, A itself is always at the origin. Every other position must be
expressed **relative to A**, so we subtract A's position from everything.

**Position of B relative to A:**

$$
\vec{r}_{B/A}(t) = \vec{r}_B(t) - \vec{r}_A(t)
$$

$$
= (t,\ -2t) - (3t,\ t)
$$

$$
x_{B/A} = t - 3t = -2t
$$

$$
y_{B/A} = -2t - t = -3t
$$

$$
\boxed{\vec{r}_{B/A}(t) = (-2t,\ -3t)}
$$

**Velocity of B as seen from A:**

$$
\vec{v}_{B/A} = \frac{d\vec{r}_{B/A}}{dt} = (-2,\ -3)\ \text{m/s}
$$

This is indeed $\vec{v}_B - \vec{v}_A = (1,-2)-(3,1) = (-2,-3)$ ✓

**Trajectory in A's frame:**

Since $x_{B/A} = -2t$ and $y_{B/A} = -3t$, eliminate $t$:

$$
t = -\frac{x_{B/A}}{2} \implies y_{B/A} = -3\cdot\left(-\frac{x_{B/A}}{2}\right) = \frac{3}{2}x_{B/A}
$$

$$
\text{Trajectory (A's frame): } y = \frac{3}{2}x
$$

From A's perspective, B moves in a **straight line** with slope $3/2$,
heading into the **third quadrant** (both $x$ and $y$ decrease over time —
B moves to the lower-left as seen from A).

**Position table (A's frame):**

| $t\ (\text{s})$ | $\vec{r}_{B/A} = (-2t,\ -3t)$ | Description |
|:---:|:---:|:---|
| $0$ | $(0,\ 0)$ | B starts at A |
| $1$ | $(-2,\ -3)$ | B moves lower-left |
| $2$ | $(-4,\ -6)$ | B continues lower-left |
| $3$ | $(-6,\ -9)$ | B further lower-left |

> **Explanation:**
> To switch to A's reference frame, imagine you are sitting on A and cannot
> feel your own motion. Everything around you appears to move as if A were
> stationary. Mathematically, you subtract A's position from all positions.
> From A's perspective, B is drifting steadily away toward the lower-left.
> The relative motion is still a straight line (because both original motions
> are constant velocity), but the direction is completely different from what
> either body looks like in the lab frame. The slope $3/2$ matches the direction
> of $\vec{v}_{B/A} = (-2, -3)$: going $2$ left and $3$ down gives slope
> $(-3)/(-2) = 3/2$.

---

### Frame 3 – Reference frame attached to body B

**Question:** What does the motion of A look like to an observer riding on B?

**Solution:**

In B's frame, B itself is always at the origin. Express everything relative to B.

**Position of A relative to B:**

$$
\vec{r}_{A/B}(t) = \vec{r}_A(t) - \vec{r}_B(t)
$$

$$
= (3t,\ t) - (t,\ -2t)
$$

$$
x_{A/B} = 3t - t = 2t
$$

$$
y_{A/B} = t - (-2t) = t + 2t = 3t
$$

$$
\boxed{\vec{r}_{A/B}(t) = (2t,\ 3t)}
$$

**Velocity of A as seen from B:**

$$
\vec{v}_{A/B} = \frac{d\vec{r}_{A/B}}{dt} = (2,\ 3)\ \text{m/s}
$$

This matches Question 8.1: $\vec{v}_{A/B} = \vec{v}_A - \vec{v}_B = (2, 3)$ ✓

**Trajectory in B's frame:**

Since $x_{A/B} = 2t$ and $y_{A/B} = 3t$, eliminate $t$:

$$
t = \frac{x_{A/B}}{2} \implies y_{A/B} = 3\cdot\frac{x_{A/B}}{2} = \frac{3}{2}x_{A/B}
$$

$$
\text{Trajectory (B's frame): } y = \frac{3}{2}x
$$

From B's perspective, A moves in a **straight line** with slope $3/2$,
heading into the **first quadrant** (both $x$ and $y$ increase — A moves
to the upper-right as seen from B).

**Position table (B's frame):**

| $t\ (\text{s})$ | $\vec{r}_{A/B} = (2t,\ 3t)$ | Description |
|:---:|:---:|:---|
| $0$ | $(0,\ 0)$ | A starts at B |
| $1$ | $(2,\ 3)$ | A moves upper-right |
| $2$ | $(4,\ 6)$ | A continues upper-right |
| $3$ | $(6,\ 9)$ | A further upper-right |

> **Explanation:**
> Now we sit on B and watch A. A drifts steadily away toward the upper-right.
> Again it is a straight line — relative motion between two constant-velocity
> bodies is always a straight line. Notice that the trajectory slope $3/2$ is
> the same in both A's frame and B's frame. This is because the direction of
> relative motion is the same whether you compute A-relative-to-B or
> B-relative-to-A — only the direction (sign) flips, not the slope of the line.
> The speed of A seen from B is $|\vec{v}_{A/B}| = \sqrt{13} \approx 3.61$ m/s,
> which equals the speed of B seen from A (as computed in 8.1) — again
> confirming that relative speed is symmetric.

---

### Summary of all three frames

| Frame | A's trajectory | B's trajectory | Relative motion |
|:---|:---:|:---:|:---|
| Lab (origin) | $y = \frac{1}{3}x$, upper-right | $y = -2x$, lower-right | Diverge from origin |
| A's frame | A fixed at origin | $y = \frac{3}{2}x$, lower-left | B moves away from A |
| B's frame | $y = \frac{3}{2}x$, upper-right | B fixed at origin | A moves away from B |

All trajectories are **straight lines** because both velocities are constant
(no acceleration in this problem).

---

## Possible Questions and Answers

**Q1: Is relative velocity commutative? Is $\vec{v}_{A/B}$ the same as $\vec{v}_{B/A}$?**

A: No, relative velocity is not commutative — the two are equal and opposite:
$\vec{v}_{A/B} = -\vec{v}_{B/A}$. Here $\vec{v}_{A/B} = (2, 3)$ and
$\vec{v}_{B/A} = (-2, -3)$. They have the same magnitude $\sqrt{13}$ but
point in opposite directions. This makes physical sense: if A moves away
from B at $3.61$ m/s to the upper-right, then B moves away from A at
$3.61$ m/s to the lower-left — just the mirror image.

---

**Q2: Why are all trajectories in all three frames straight lines?**

A: Because both bodies move with **constant velocity** (no acceleration).
When you subtract two constant-velocity motions, you get another constant-velocity
motion: $\vec{r}_{A/B}(t) = (\vec{v}_A - \vec{v}_B)t$, which is a linear
function of $t$ — a straight line in the plane. If either body had acceleration,
the relative trajectory could be curved (a parabola, circle, etc.). Constant
velocity always gives straight-line trajectories in any inertial reference frame.

---

**Q3: What would the motion look like in B's frame if B had the same velocity
as A?**

A: If $\vec{v}_B = \vec{v}_A = (3, 1)$, then $\vec{v}_{A/B} = \vec{v}_A - \vec{v}_B = (0, 0)$.
In B's frame, A would appear completely stationary — it would just sit at a
fixed point and never move. This is the principle behind formation flying or
convoy driving: vehicles moving at identical velocities appear motionless
relative to each other, even though they are all moving fast in the lab frame.

---

**Q4: Does the choice of reference frame affect the physics — for example,
does the relative velocity between A and B change depending on which frame
you observe from?**

A: The relative velocity $\vec{v}_{A/B}$ is the same regardless of which
inertial frame you observe from (lab frame, A's frame, B's frame, or any
other frame moving at constant velocity). This is because changing frames
adds the same constant velocity to everything, which cancels in the
subtraction $\vec{v}_A - \vec{v}_B$. What does change between frames is
the individual velocities $\vec{v}_A$ and $\vec{v}_B$ — those depend on
your frame of reference. Only differences (relative velocities) are
frame-independent in classical mechanics.

---

**Q5: How would this problem change if the two bodies did not start at
the same position?**

A: If the initial positions were $\vec{r}_A(0) = \vec{r}_{A0}$ and
$\vec{r}_B(0) = \vec{r}_{B0}$ with $\vec{r}_{A0} \neq \vec{r}_{B0}$,
then the relative position would be:
$$
\vec{r}_{A/B}(t) = (\vec{r}_{A0} - \vec{r}_{B0}) + (\vec{v}_A - \vec{v}_B)t
$$
The trajectory is still a straight line (because velocities are still constant),
but it no longer passes through the origin. The relative velocity $\vec{v}_{A/B}$
is unchanged — it depends only on velocities, not on initial positions. The
initial separation $\vec{r}_{A0} - \vec{r}_{B0}$ just shifts the starting
point of the relative trajectory.