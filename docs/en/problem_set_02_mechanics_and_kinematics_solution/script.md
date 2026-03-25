# Presentation Monologue Script
## Problem 3 — Elimination of Time and Interpretation of Acceleration

---

> **How to read this script:**
> - Text in **(parentheses)** tells you how to say the mathematical symbol out loud.
> - **[Stage directions]** tell you what to point at or do on screen.
> - Pause at each "..." for a breath.

---

## Opening

"Good morning everyone. Today I am presenting Problem 3, which is about the Elimination of Time and Interpretation of Acceleration.

We are given a path described in **parametric form** — meaning we have two equations, one for $x$ and one for $y$, both in terms of $t$. 

The variable $t$ represents time — so as $t$ increases, a particle moves along a path in the $xy$-plane. Our job is to understand the shape of that path and describe how the particle moves along it."

---

## Question 3.1 — Eliminating the parameter

"The first question asks us to **eliminate $t$** — that is, to find a direct relationship between $y$ and $x$ with no $t$ in it.

[Point to the Step 1 block]

**Step 1.** We start with the $x$ equation: $x$ equals $2t$ squared (x equals 2 t squared). We solve for $t$ by dividing both sides by 2, giving $t$ squared equals $x$ over $2$ (t squared equals x over 2). 

I will not be explaining every step since I believe we should know how this would work, but eventually, we will derive with t equals the square root of $x$ over $2$ (t equals the square root of x over 2), or equivalently, $t$ equals $x$ over $2$ to the power of one half (x over 2, to the power one half).

[Point to the Step 2 block]

**Step 2.** We need $t$ cubed for the $y$ equation, but we only have $t$ squared from the step above. The trick is to write $t$ cubed as $t$ squared times $t$ (t cubed equals t squared times t). So $t$ cubed equals $x$ over $2$, times $x$ over $2$ to the one half... which gives us $x$ over $2$ to the three halves (x over 2, to the power three halves).

[Point to the Step 3 block]

**Step 3.** Now we substitute into $y$ equals $3t$ cubed (y equals 3 t cubed). We replace $t$ cubed with what we just found: $y$ equals $3$ times $x$ over $2$, to the three halves (3 times x over 2, to the three halves).

[Point to the final result box]

**Simplification.** We simplify the coefficient. $2$ to the three halves (2 to the three halves) equals $2$ times $\sqrt{2}$ (2 times root 2), which equals $2\sqrt{2}$. So the fraction $3$ over $2$ to the three halves (3 over 2 to the three halves) becomes $3$ over $2\sqrt{2}$... and after rationalising by multiplying top and bottom by $\sqrt{2}$... we get $3\sqrt{2}$ over $4$ (3 root 2 over 4).

The final result is: $y$ equals $3\sqrt{2}$ over $4$, times $x$ to the power $3$ over $2$ (y equals 3 root 2, over 4, times x to the power three halves).

This is valid only for $x \geq 0$ (x greater than or equal to zero), because $x = 2t^2$ (x equals 2 t squared) is always non-negative.

This type of curve is called a **power-law curve** — it looks somewhat like a parabola but grows a bit faster. The exponent $3/2$ (three halves) is between 1 and 2, so the curve bends more gradually than a parabola."

---

## Question 3.2 — Drawing the trajectory

"Now let's look at the **trajectory** of the curve y.

[Enable the Curve toggle on the visualisation]

I will compute a few specific points using the original parametric equations.

[Point to the table on screen]

At $t$ equals $0$: both $x$ and $y$ are zero — the particle is at the **origin**.

At $t$ equals $1$: $x$ equals $2$ times $1$ squared equals $2$ (x equals 2 times 1 squared equals 2), and $y$ equals $3$ times $1$ cubed equals $3$ (y equals 3 times 1 cubed equals 3). So the point is $(2, 3)$ (the point 2 comma 3).

At $t$ equals $-1$ (t equals negative 1): $x$ equals $2$ times $(-1)$ squared, which is still $2$ (x is still 2), but $y$ equals $3$ times $(-1)$ cubed equals $-3$ (y equals negative 3). So the point is $(2, -3)$ (the point 2 comma negative 3).

[Gesture at the blue curve above the axis and the pink dashed curve below]

Notice something important: for $t > 0$ (t greater than zero), the curve is in the **upper right** quadrant. For $t < 0$ (t less than zero), the curve is in the **lower right** quadrant. And because $x = 2t^2$ (x equals 2 t squared) is the same for $+t$ and $-t$ (positive t and negative t), but $y = 3t^3$ (y equals 3 t cubed) flips sign, the curve is **symmetric about the $x$-axis**.

[Point to the white dot at the origin]

The special point at the origin — where $t$ equals $0$ — is called a **cusp**. It is a sharp point on the curve where the particle momentarily comes to a complete stop before reversing its $y$-direction. We will prove this in the next section."

---

## Question 3.3 — Velocity and acceleration

"Now we calculate the velocity and acceleration vectors by **differentiating** the position.

[Point to the velocity result card]

**Velocity.** The velocity vector $\vec{v}$ of $t$ (v of t) has two components: $v_x$ (v sub x) is the derivative of $x$ with respect to $t$ (derivative of x with respect to t). Since $x = 2t^2$ (x equals 2 t squared), we get $v_x = 4t$ (v sub x equals 4t). Similarly, $v_y$ (v sub y) is the derivative of $y = 3t^3$ (y equals 3 t cubed), which gives $v_y = 9t^2$ (v sub y equals 9 t squared).

So the velocity vector is $\vec{v}(t) = (4t, \ 9t^2)$ (v of t equals the vector 4t comma 9 t squared).

[Point to the speed result card]

**Speed.** The magnitude of the velocity — which is the speed — is found using the Pythagorean formula on the two components. 

Then we factor out t2 from under the square root,

giving us the final result: speed equals $|t|$ times $\sqrt{16 + 81t^2}$ (absolute value of t, times square root of 16 plus 81 t squared).

[Pause and point to the cusp annotation]

At $t = 0$ (t equals zero): speed equals $0$ times $\sqrt{16}$ (zero times square root of 16), which equals **zero**. This confirms the diagram I showed earlier that the particle has zero speed at the origin.

[Point to the acceleration result card]

**Acceleration.** We differentiate the velocity vector to get acceleration. $a_x$ (a sub x) is the derivative of $v_x = 4t$ (v sub x equals 4t), giving $a_x = 4$ (a sub x equals 4). $a_y$ (a sub y) is the derivative of $v_y = 9t^2$ (v sub y equals 9 t squared), giving $a_y = 18t$ (a sub y equals 18 t).

So the acceleration vector is $\vec{a}(t) = (4, \ 18t)$ (a of t equals the vector 4 comma 18t).

And the magnitude of acceleration is $\sqrt{16 + 324t^2}$ (square root of 16 plus 324 t squared).

[Enable the velocity and acceleration toggles on the visualisation and drag the slider]

You can see here on the visualisation — as I move $t$ (as I move t), the velocity arrow in green changes both direction and length, while the acceleration arrow in pink always has the same horizontal component but its vertical component tilts more and more."

---

## Question 3.4 — Is the acceleration constant?

"The final question asks whether the acceleration is **constant**.

[Point to the component analysis card]

Let's check each component separately.

The horizontal component $a_x = 4$ (a sub x equals 4). This is a plain number — it does not depend on $t$ at all. So the horizontal acceleration is **constant**. The particle is always being pushed in the $x$-direction with the same strength.

The vertical component $a_y = 18t$ (a sub y equals 18 t). This clearly depends on $t$ — it is zero when $t = 0$ (t equals zero), positive and growing for $t > 0$ (t greater than zero), and negative and growing in magnitude for $t < 0$ (t less than zero).

[Point to the table of values]

For example, at $t = 1$: $\vec{a} = (4, 18)$ (a equals the vector 4 comma 18), with magnitude approximately $18.4$. At $t = 2$: $\vec{a} = (4, 36)$ (a equals the vector 4 comma 36), with magnitude approximately $36.2$. The acceleration is getting larger and tilting more steeply upward.

[Point to the red verdict badge]

**Conclusion:** Since the $y$-component changes with time, the acceleration vector changes both its direction and its magnitude. Therefore, $\vec{a}(t)$ is **not constant**.

This is different from projectile motion, where the acceleration is truly constant: $(0, -g)$ (zero comma negative g). Here the vertical acceleration keeps growing — there is no fixed gravitational-like force. The motion in the two directions cannot be treated as two simple constant-acceleration problems independently."

---

## Closing

"To summarise what we found in Problem 3:

- The parametric curve $x = 2t^2$, $y = 3t^3$ (x equals 2 t squared, y equals 3 t cubed) traces a power-law curve $y = \frac{3\sqrt{2}}{4} x^{3/2}$ (y equals 3 root 2 over 4, times x to the three halves), symmetric about the $x$-axis, with a cusp at the origin.
- The velocity vector is $(4t, \ 9t^2)$ (the vector 4t comma 9 t squared) and the speed is $|t|\sqrt{16 + 81t^2}$ (absolute value of t, times square root of 16 plus 81 t squared). Speed is zero at the cusp.
- The acceleration vector is $(4, \ 18t)$ (the vector 4 comma 18t). The horizontal component is constant, but the vertical component grows with time, so the acceleration is **not constant**.

Thank you."