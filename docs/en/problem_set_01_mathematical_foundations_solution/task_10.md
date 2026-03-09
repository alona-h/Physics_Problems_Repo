# Problem Set 1 – Problem 10: Angular Momentum in Circular Motion

---

## Overview

This problem studies **circular motion** and one of the most fundamental conserved quantities in physics: **angular momentum**. Angular momentum is the rotational analogue of linear momentum — while linear momentum $\vec{p} = m\vec{v}$ measures "how much straight-line motion" an object has, angular momentum $\vec{L} = m\,\vec{r} \times \vec{v}$ measures "how much rotational motion" it has about a chosen point.

> **Key concepts introduced:**
> - $\vec{r}(t)$ — position vector describing circular motion
> - $\vec{v}(t) = \dot{\vec{r}}(t)$ — velocity (tangent to the circle)
> - $\vec{L}(t) = m\,\vec{r}(t) \times \vec{v}(t)$ — angular momentum
> - $\vec{\tau} = \vec{r} \times \vec{F}$ — torque (the "rotational force")
> - $\vec{\tau} = \frac{d\vec{L}}{dt}$ — Newton's second law for rotation

**Given circular motion:**
$$\vec{r}(t) = \bigl(R\cos(\omega t),\ R\sin(\omega t),\ 0\bigr)$$

where $R$ is the radius of the circle and $\omega$ is the angular frequency (radians per second).

---

## 10.1 – Velocity $\vec{v}(t) = \dot{\vec{r}}(t)$

Differentiate each component of $\vec{r}(t)$ with respect to $t$:

$$\vec{v}(t) = \frac{d\vec{r}}{dt} = \left(\frac{d}{dt}(R\cos(\omega t)),\ \frac{d}{dt}(R\sin(\omega t)),\ \frac{d}{dt}(0)\right)$$

**Component by component:**
- $\frac{d}{dt}(R\cos(\omega t)) = -R\omega\sin(\omega t)$
- $\frac{d}{dt}(R\sin(\omega t)) = R\omega\cos(\omega t)$
- $\frac{d}{dt}(0) = 0$

$$\boxed{\vec{v}(t) = \bigl(-R\omega\sin(\omega t),\ R\omega\cos(\omega t),\ 0\bigr)}$$

**Speed:**
$$|\vec{v}(t)| = \sqrt{(-R\omega\sin(\omega t))^2 + (R\omega\cos(\omega t))^2 + 0}$$
$$= R\omega\sqrt{\sin^2(\omega t) + \cos^2(\omega t)} = R\omega$$

The speed is **constant** — this confirms uniform circular motion.

**Verify $\vec{v} \perp \vec{r}$ (velocity is tangent to the circle):**
$$\vec{r} \cdot \vec{v} = (R\cos\omega t)(-R\omega\sin\omega t) + (R\sin\omega t)(R\omega\cos\omega t) + 0$$
$$= -R^2\omega\cos\omega t\sin\omega t + R^2\omega\sin\omega t\cos\omega t = 0 \checkmark$$

> **Explanation:** The velocity is always tangent to the circle — perpendicular to the radius vector $\vec{r}$. This is why the speed stays constant: the "force" keeping the object on the circle (centripetal force) acts inward along $\vec{r}$, always perpendicular to $\vec{v}$, so it never does work and never changes the speed. The factor $R\omega$ in the speed makes physical sense: a larger circle ($R$) or faster rotation ($\omega$) both increase the speed.

---

## 10.2 – Angular momentum $\vec{L}(t) = m\,\vec{r}(t) \times \vec{v}(t)$

The angular momentum is the cross product of position and momentum:
$$\vec{L}(t) = m\,\vec{r}(t) \times \vec{v}(t)$$

**Set up the cross product:**

$$\vec{r} \times \vec{v} = \begin{vmatrix} \vec{i} & \vec{j} & \vec{k} \\ R\cos(\omega t) & R\sin(\omega t) & 0 \\ -R\omega\sin(\omega t) & R\omega\cos(\omega t) & 0 \end{vmatrix}$$

**Expanding along the first row:**

**$\vec{i}$-component:**
$$i: \quad (R\sin(\omega t))(0) - (0)(R\omega\cos(\omega t)) = 0$$

**$\vec{j}$-component:**
$$j: \quad -\left[(R\cos(\omega t))(0) - (0)(-R\omega\sin(\omega t))\right] = 0$$

**$\vec{k}$-component:**
$$k: \quad (R\cos(\omega t))(R\omega\cos(\omega t)) - (R\sin(\omega t))(-R\omega\sin(\omega t))$$
$$= R^2\omega\cos^2(\omega t) + R^2\omega\sin^2(\omega t)$$
$$= R^2\omega\underbrace{(\cos^2(\omega t) + \sin^2(\omega t))}_{=1}$$
$$= R^2\omega$$

**Therefore:**
$$\vec{r} \times \vec{v} = (0,\ 0,\ R^2\omega)$$

**Including mass $m$:**
$$\boxed{\vec{L}(t) = m\,\vec{r}(t) \times \vec{v}(t) = (0,\ 0,\ mR^2\omega)}$$

> **Explanation:** The angular momentum vector is constant — it does not depend on $t$ at all. It points purely in the $z$-direction, perpendicular to the $xy$-plane in which the motion takes place. This makes perfect geometric sense: the cross product of two vectors in the $xy$-plane always points along the $z$-axis. The magnitude $mR^2\omega$ tells us that angular momentum grows with mass (heavier objects have more), with the square of the radius (doubling the radius quadruples the angular momentum), and with angular speed.

---

## 10.3 – Show that $|\vec{L}| = mR^2\omega$ is constant and $\vec{L} \perp$ plane of motion

**Magnitude:**
$$|\vec{L}| = \sqrt{0^2 + 0^2 + (mR^2\omega)^2} = mR^2\omega$$

Since $m$, $R$, and $\omega$ are all constants, $|\vec{L}|$ is **constant** — it does not depend on time $t$.

$$\boxed{|\vec{L}| = mR^2\omega = \text{const}}$$

**Direction:**

The vector $\vec{L} = (0, 0, mR^2\omega)$ points entirely along the $z$-axis. The motion $\vec{r}(t) = (R\cos\omega t, R\sin\omega t, 0)$ lies entirely in the $xy$-plane (the $z$-component is always $0$). Since the $z$-axis is perpendicular to the $xy$-plane:

$$\boxed{\vec{L} \perp \text{plane of motion (the } xy\text{-plane)}}$$

**Alternative derivation using $|\vec{L}| = |\vec{r}||\vec{v}|\sin\theta$:**

The angle between $\vec{r}$ and $\vec{v}$ is always $\theta = 90°$ (they are perpendicular, as shown in 10.1). Therefore:
$$|\vec{L}| = m|\vec{r}||\vec{v}|\sin(90°) = m \cdot R \cdot R\omega \cdot 1 = mR^2\omega \checkmark$$

**Why is $\vec{L}$ conserved?**

Angular momentum is conserved when the **torque** $\vec{\tau} = \frac{d\vec{L}}{dt}$ is zero. Since $\vec{L}$ is constant:
$$\vec{\tau} = \frac{d\vec{L}}{dt} = \frac{d}{dt}(0, 0, mR^2\omega) = (0, 0, 0) = \vec{0}$$

And indeed the centripetal force points along $\vec{r}$ (radially inward), so $\vec{\tau} = \vec{r} \times \vec{F}_c = \vec{0}$ since $\vec{r} \parallel \vec{F}_c$ (parallel vectors have zero cross product).

> **Explanation:** Angular momentum is conserved whenever there is no net torque. Here, the only force is centripetal — it points exactly toward the centre (along $-\vec{r}$), so it is parallel to $\vec{r}$. A force parallel to the position vector produces zero torque: $\vec{r} \times \vec{F} = \vec{0}$ because the angle between them is $0°$ (or $180°$), and $\sin(0°) = \sin(180°) = 0$. This is why planets conserve angular momentum — gravity pulls them toward the Sun (along $\vec{r}$), so the torque is zero and $\vec{L}$ never changes.

---

## 10.4 – Direction of $\vec{L}$: right-hand rule

The angular momentum $\vec{L} = (0, 0, mR^2\omega)$ points in the **positive $z$-direction** (assuming $\omega > 0$).

**Right-hand rule interpretation:**

To find the direction of $\vec{r} \times \vec{v}$:
1. Point the fingers of your **right hand** in the direction of $\vec{r}$ (outward from the centre)
2. **Curl** your fingers toward $\vec{v}$ (in the direction of motion — counterclockwise for $\omega > 0$)
3. Your **thumb** points in the direction of $\vec{L}$ — straight **upward** (positive $z$)

If $\omega > 0$: motion is **counterclockwise** when viewed from above → $\vec{L}$ points **upward** ($+z$)

If $\omega < 0$: motion is **clockwise** when viewed from above → $\vec{L}$ points **downward** ($-z$)

> **Explanation:** The right-hand rule is a convention that assigns a consistent direction to rotation. Think of a spinning top or a wheel: the angular momentum vector points along the spin axis in the direction your right thumb points when your fingers curl in the direction of rotation. This is why gyroscopes resist tipping — their large $\vec{L}$ vector "wants" to keep pointing in the same direction (conservation of angular momentum), and any external torque needed to change it is strongly resisted.

---

## 10.5 – (Optional) Centripetal force, torque, and verification of $\vec{\tau} = \frac{d\vec{L}}{dt}$

### Centripetal force

For circular motion, the required centripetal force points toward the centre:
$$\vec{F}_c = -m\omega^2\vec{r}(t) = -m\omega^2\bigl(R\cos(\omega t),\ R\sin(\omega t),\ 0\bigr)$$

$$= \bigl(-mR\omega^2\cos(\omega t),\ -mR\omega^2\sin(\omega t),\ 0\bigr)$$

**Magnitude:** $|\vec{F}_c| = mR\omega^2 = \frac{mv^2}{R}$ (standard centripetal force formula)

> **Explanation:** The centripetal force is not a new kind of force — it is whatever force (gravity, tension, normal force, etc.) happens to be providing the inward pull. For a satellite, it is gravity. For a ball on a string, it is tension. The formula $F_c = mR\omega^2 = mv^2/R$ tells us how much inward force is needed to keep the object moving in a circle of radius $R$ at speed $v = R\omega$.

---

### Torque $\vec{\tau} = \vec{r} \times \vec{F}_c$

$$\vec{\tau} = \vec{r}(t) \times \vec{F}_c(t)$$

$$= \begin{vmatrix} \vec{i} & \vec{j} & \vec{k} \\ R\cos(\omega t) & R\sin(\omega t) & 0 \\ -mR\omega^2\cos(\omega t) & -mR\omega^2\sin(\omega t) & 0 \end{vmatrix}$$

**$\vec{i}$-component:** $(R\sin\omega t)(0) - (0)(-mR\omega^2\sin\omega t) = 0$

**$\vec{j}$-component:** $-[(R\cos\omega t)(0) - (0)(-mR\omega^2\cos\omega t)] = 0$

**$\vec{k}$-component:**
$$(R\cos\omega t)(-mR\omega^2\sin\omega t) - (R\sin\omega t)(-mR\omega^2\cos\omega t)$$
$$= -mR^2\omega^2\cos\omega t\sin\omega t + mR^2\omega^2\sin\omega t\cos\omega t = 0$$

$$\boxed{\vec{\tau} = \vec{r} \times \vec{F}_c = (0, 0, 0) = \vec{0}}$$

The torque is zero because $\vec{F}_c \parallel -\vec{r}$ — the force is antiparallel to the position vector.

---

### Verification: $\vec{\tau} = \frac{d\vec{L}}{dt}$

From section 10.2, we found:
$$\vec{L}(t) = (0,\ 0,\ mR^2\omega) = \text{constant vector}$$

Differentiating:
$$\frac{d\vec{L}}{dt} = \frac{d}{dt}(0,\ 0,\ mR^2\omega) = (0,\ 0,\ 0) = \vec{0}$$

Since $\vec{\tau} = \vec{0}$ and $\frac{d\vec{L}}{dt} = \vec{0}$:

$$\boxed{\vec{\tau} = \frac{d\vec{L}}{dt} = \vec{0}} \checkmark$$

This verifies Newton's second law for rotation: **zero torque ↔ constant angular momentum**.

> **Explanation:** This is the rotational analogue of Newton's first law: just as a particle with no net force moves in a straight line at constant speed (constant $\vec{p}$), a particle with no net torque rotates with constant angular momentum. The law $\vec{\tau} = d\vec{L}/dt$ is one of the most powerful statements in mechanics — it is the basis for understanding everything from spinning tops to the precession of the Earth's axis to the way a figure skater speeds up by pulling their arms in.

---

## Summary Table

| Quantity | Expression | Value / Notes |
|---|---|---|
| Position | $\vec{r}(t) = (R\cos\omega t,\ R\sin\omega t,\ 0)$ | Circle of radius $R$ in $xy$-plane |
| Velocity | $\vec{v}(t) = (-R\omega\sin\omega t,\ R\omega\cos\omega t,\ 0)$ | Always $\perp$ to $\vec{r}$ |
| Speed | $\|\vec{v}\| = R\omega$ | Constant |
| Acceleration | $\vec{a}(t) = -\omega^2\vec{r}(t)$ | Centripetal, points toward centre |
| Centripetal force | $\vec{F}_c = -m\omega^2\vec{r}$ | Magnitude $mR\omega^2 = mv^2/R$ |
| Angular momentum | $\vec{L} = (0,\ 0,\ mR^2\omega)$ | Constant, points along $+z$ |
| Magnitude $\|\vec{L}\|$ | $mR^2\omega$ | Constant — conserved |
| Direction of $\vec{L}$ | $+z$-axis (for $\omega > 0$) | $\perp$ to plane of motion |
| Torque | $\vec{\tau} = \vec{r} \times \vec{F}_c = \vec{0}$ | Zero — force is radial |
| $d\vec{L}/dt$ | $\vec{0}$ | Confirms $\vec{\tau} = d\vec{L}/dt$ |

---

## 5 Possible Questions & Answers

---

**Q1: Why is angular momentum defined as $\vec{L} = m\,\vec{r} \times \vec{v}$ rather than just $mrv$? What does the cross product add?**

**A:** The scalar product $mrv$ gives only the magnitude of angular momentum in the special case where $\vec{r}$ and $\vec{v}$ are perpendicular (as in circular motion). In general, the cross product $\vec{r} \times \vec{v}$ is needed because it: (1) automatically captures the $\sin\theta$ factor — only the component of velocity perpendicular to $\vec{r}$ contributes to rotation ($L = mrv\sin\theta$); (2) gives a **direction** — the axis of rotation, which is essential for 3D problems; (3) is zero when $\vec{r} \parallel \vec{v}$ (radial motion has no angular momentum), which is physically correct. A purely radial motion (straight toward or away from the origin) creates no rotation, so its angular momentum must be zero — and the cross product of parallel vectors is indeed zero.

---

**Q2: A figure skater pulls their arms in, reducing their moment of inertia from $I_1$ to $I_2 < I_1$. Using conservation of angular momentum, find their new angular speed.**

**A:** Angular momentum is $L = I\omega$ (for a rigid body, where $I$ is the moment of inertia). Since no external torque acts on the skater during the arm pull, $\vec{L}$ is conserved:
$$L_1 = L_2 \implies I_1\omega_1 = I_2\omega_2$$
$$\omega_2 = \frac{I_1}{I_2}\omega_1$$
Since $I_2 < I_1$, we have $\omega_2 > \omega_1$ — the skater spins faster. For example, if the skater reduces their moment of inertia by half ($I_2 = I_1/2$), their angular speed doubles ($\omega_2 = 2\omega_1$). This is a direct consequence of $\vec{\tau} = d\vec{L}/dt = 0$ — the same principle that governs planetary motion, gyroscopes, and diving rotations.

---

**Q3: Show directly from the definitions that $\vec{r}(t) \times \vec{v}(t)$ is perpendicular to $\vec{r}(t)$ and to $\vec{v}(t)$.**

**A:** By the fundamental property of the cross product, $\vec{A} \times \vec{B}$ is always perpendicular to both $\vec{A}$ and $\vec{B}$. We can verify explicitly: $\vec{r} \cdot (\vec{r} \times \vec{v}) = (R\cos\omega t)(0) + (R\sin\omega t)(0) + (0)(R^2\omega) = 0$ ✓, and $\vec{v} \cdot (\vec{r} \times \vec{v}) = (-R\omega\sin\omega t)(0) + (R\omega\cos\omega t)(0) + (0)(R^2\omega) = 0$ ✓. Geometrically, $\vec{L}$ points along the rotation axis — perpendicular to the plane containing $\vec{r}$ and $\vec{v}$, which is the $xy$-plane. This is why angular momentum is called an **axial vector** or **pseudovector** — it points along an axis of rotation rather than along a physical direction of motion.

---

**Q4: How does the angular momentum change if the radius is doubled while keeping the speed constant?**

**A:** If the speed $v = R\omega$ is kept constant while $R$ is doubled to $2R$, the new angular frequency must halve: $\omega_{\text{new}} = v/(2R) = \omega/2$. The new angular momentum is:
$$L_{\text{new}} = m(2R)^2\omega_{\text{new}} = m \cdot 4R^2 \cdot \frac{\omega}{2} = 2mR^2\omega = 2L$$
So the angular momentum **doubles** even though the speed is unchanged. Alternatively, using $L = mRv$: $L_{\text{new}} = m(2R)v = 2mRv = 2L$. This makes physical sense: the same mass moving at the same speed, but further from the pivot point, has twice the "rotational effect." This is why a wrench is more effective when you push at the far end — the moment arm (equivalent of $R$) is larger.

---

**Q5: What is the physical significance of the relation $\vec{\tau} = \frac{d\vec{L}}{dt}$, and why is it called Newton's second law for rotation?**

**A:** Newton's second law for linear motion states $\vec{F} = \frac{d\vec{p}}{dt}$ — force equals the rate of change of linear momentum. The rotational analogue replaces force with **torque** $\vec{\tau} = \vec{r} \times \vec{F}$ (the rotational "push") and linear momentum with **angular momentum** $\vec{L} = \vec{r} \times \vec{p}$. The law $\vec{\tau} = \frac{d\vec{L}}{dt}$ then states: the net torque equals the rate of change of angular momentum. Its consequences are profound: (1) Zero torque → constant $\vec{L}$ (conservation of angular momentum — the foundation of orbital mechanics). (2) A torque perpendicular to $\vec{L}$ causes **precession** — the spin axis rotates rather than the spin slowing down (explains gyroscopes and Earth's 26,000-year axial precession). (3) The equation governs all rotational dynamics, from electric motors to black hole spin.