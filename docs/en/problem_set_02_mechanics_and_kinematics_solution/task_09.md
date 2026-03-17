# Problem 9 – Change of Reference Frame (Copernican Model → Geocentric Description)

Earth and Mars move in circles around the Sun in the same direction.

Heliocentric (Sun-centered) positions:

$$
\vec{r}_E(t) = R_E\,\bigl(\cos(\omega_E t),\ \sin(\omega_E t)\bigr)
$$

$$
\vec{r}_M(t) = R_M\,\bigl(\cos(\omega_M t),\ \sin(\omega_M t)\bigr)
$$

where:
- $R_E$ = orbital radius of Earth, $R_M$ = orbital radius of Mars
- $\omega_E$ = angular velocity of Earth, $\omega_M$ = angular velocity of Mars
- Both planets start on the positive $x$-axis at $t = 0$

**Physical values used in examples:**
- $R_E = 1\ \text{AU}$, $R_M = 1.524\ \text{AU}$
- $T_E = 1\ \text{year}$, $T_M = 1.881\ \text{years}$
- $\omega_E = \frac{2\pi}{T_E} = 2\pi\ \text{rad/year}$
- $\omega_M = \frac{2\pi}{T_M} \approx 3.340\ \text{rad/year}$

---

## Question 9.1 – Draw both motions in the heliocentric system

**Question:** Describe the trajectories of Earth and Mars as seen from the Sun,
and identify their key properties.

**Solution:**

Both planets move in **circles** centered on the Sun (the origin):

**Earth's trajectory:**

$$
|\vec{r}_E(t)| = \sqrt{R_E^2\cos^2(\omega_E t) + R_E^2\sin^2(\omega_E t)}
= R_E\sqrt{\cos^2 + \sin^2} = R_E
$$

Earth traces a circle of radius $R_E$ with period:

$$
T_E = \frac{2\pi}{\omega_E} = 1\ \text{year}
$$

**Mars's trajectory:**

$$
|\vec{r}_M(t)| = R_M = \text{const}
$$

Mars traces a circle of radius $R_M$ with period:

$$
T_M = \frac{2\pi}{\omega_M} \approx 1.881\ \text{years}
$$

**Key properties of the heliocentric picture:**

| Property | Earth | Mars |
|:---|:---:|:---:|
| Orbit shape | Circle | Circle |
| Orbital radius | $R_E = 1\ \text{AU}$ | $R_M = 1.524\ \text{AU}$ |
| Period | $1\ \text{year}$ | $1.881\ \text{years}$ |
| Angular velocity | $\omega_E = 2\pi\ \text{rad/yr}$ | $\omega_M \approx 3.340\ \text{rad/yr}$ |
| Direction | Counter-clockwise | Counter-clockwise |

**Starting positions (at $t = 0$):**

$$
\vec{r}_E(0) = R_E(\cos 0,\ \sin 0) = (R_E,\ 0)
$$

$$
\vec{r}_M(0) = R_M(\cos 0,\ \sin 0) = (R_M,\ 0)
$$

Both planets start on the positive $x$-axis — they begin in
**conjunction** (lined up on the same side of the Sun).

**Angular separation over time:**

The angle between Earth and Mars grows as:

$$
\Delta\theta(t) = \omega_E t - \omega_M t = (\omega_E - \omega_M)t
$$

Since $\omega_E > \omega_M$ (Earth orbits faster), Earth gradually laps Mars.
The time between successive conjunctions (synodic period) is:

$$
T_{\text{syn}} = \frac{2\pi}{\omega_E - \omega_M} = \frac{1}{\frac{1}{T_E} - \frac{1}{T_M}}
= \frac{T_E \cdot T_M}{T_M - T_E} \approx \frac{1 \times 1.881}{1.881 - 1} \approx 2.135\ \text{years}
$$

> **Explanation:**
> In the heliocentric (Sun-centered) picture, everything is beautifully simple:
> both planets just go around the Sun in circles at their own constant speeds.
> Earth is closer to the Sun so it moves faster ($\omega_E > \omega_M$) and
> completes one full orbit in less time. Mars is farther out, moves more slowly,
> and takes almost two Earth-years to complete one orbit. Both start at the
> same angle (positive $x$-axis), but Earth quickly pulls ahead. After about
> $2.135$ years Earth has lapped Mars and they are aligned again — this is
> called a synodic period. The heliocentric picture was Copernicus's great
> insight: the Solar System looks simple and orderly when you put the Sun in
> the center.

---

## Question 9.2 – Determine the position of Mars relative to Earth

**Question:** Write down the position of Mars as seen from Earth —
the geocentric description.

### Definition of relative position

$$
\vec{r}_{M/E}(t) = \vec{r}_M(t) - \vec{r}_E(t)
$$

### Step-by-step calculation

Substitute the heliocentric positions:

$$
\vec{r}_{M/E}(t) = R_M\bigl(\cos(\omega_M t),\ \sin(\omega_M t)\bigr)
- R_E\bigl(\cos(\omega_E t),\ \sin(\omega_E t)\bigr)
$$

Subtract component by component:

**$x$-component:**

$$
x_{M/E}(t) = R_M\cos(\omega_M t) - R_E\cos(\omega_E t)
$$

**$y$-component:**

$$
y_{M/E}(t) = R_M\sin(\omega_M t) - R_E\sin(\omega_E t)
$$

$$
\boxed{
\vec{r}_{M/E}(t) = \bigl(
R_M\cos(\omega_M t) - R_E\cos(\omega_E t),\
R_M\sin(\omega_M t) - R_E\sin(\omega_E t)
\bigr)
}
$$

### Numerical example at selected times

Using $R_E = 1$, $R_M = 1.524$, $\omega_E = 2\pi$, $\omega_M = 2\pi/1.881$
(in AU and years):

**At $t = 0$ (conjunction — both on same side of Sun):**

$$
x_{M/E}(0) = 1.524\cos(0) - 1\cos(0) = 1.524 - 1 = 0.524\ \text{AU}
$$

$$
y_{M/E}(0) = 1.524\sin(0) - 1\sin(0) = 0
$$

$$
\vec{r}_{M/E}(0) = (0.524,\ 0)\ \text{AU}
$$

Mars is $0.524$ AU directly to the right of Earth.

**At $t = T_E/4 = 0.25\ \text{years}$:**

$$
\omega_E t = 2\pi \cdot 0.25 = \frac{\pi}{2}, \qquad
\omega_M t = \frac{2\pi}{1.881} \cdot 0.25 \approx 0.836\ \text{rad}
$$

$$
x_{M/E} = 1.524\cos(0.836) - 1\cos(\pi/2) \approx 1.524(0.670) - 0 \approx 1.021\ \text{AU}
$$

$$
y_{M/E} = 1.524\sin(0.836) - 1\sin(\pi/2) \approx 1.524(0.742) - 1 \approx 0.131\ \text{AU}
$$

**Distance from Earth to Mars over time:**

$$
|\vec{r}_{M/E}(t)| = \sqrt{(R_M\cos(\omega_M t) - R_E\cos(\omega_E t))^2
+ (R_M\sin(\omega_M t) - R_E\sin(\omega_E t))^2}
$$

Expand using $\cos^2 + \sin^2 = 1$:

$$
= \sqrt{R_M^2 + R_E^2 - 2R_M R_E\cos((\omega_M - \omega_E)t)}
$$

$$
\boxed{|\vec{r}_{M/E}(t)| = \sqrt{R_M^2 + R_E^2 - 2R_M R_E\cos((\omega_M - \omega_E)t)}}
$$

**Maximum distance** (opposition — planets on opposite sides of Sun,
$\cos = -1$):

$$
|\vec{r}_{M/E}|_{\max} = \sqrt{R_M^2 + R_E^2 + 2R_M R_E}
= R_M + R_E = 1.524 + 1 = 2.524\ \text{AU}
$$

**Minimum distance** (conjunction — planets on same side of Sun,
$\cos = +1$):

$$
|\vec{r}_{M/E}|_{\min} = \sqrt{R_M^2 + R_E^2 - 2R_M R_E}
= |R_M - R_E| = 1.524 - 1 = 0.524\ \text{AU}
$$

> **Explanation:**
> To find where Mars is "as seen from Earth," we simply subtract Earth's
> position vector from Mars's position vector. This is the same subtraction
> used in Problem 8 for relative motion — the principle is identical. The
> result is a vector that points from Earth to Mars, with a length equal to
> the Earth–Mars distance. When both planets are on the same side of the Sun
> (conjunction), they are closest ($0.524$ AU apart). When they are on
> opposite sides (opposition), they are farthest ($2.524$ AU apart). The
> distance formula $\sqrt{R_M^2 + R_E^2 - 2R_MR_E\cos(\Delta\theta)}$ is
> just the **law of cosines** applied to the triangle Sun–Earth–Mars.

---

## Question 9.3 – HTML Animation with two panels

**Question:** Describe what the two-panel animation shows and how it
connects the heliocentric and geocentric views.

### Panel A — Heliocentric motion

**What is shown:**

- The **Sun** at the center (origin), drawn as a yellow circle
- **Earth** orbiting the Sun in a circle of radius $R_E$:
  $$
  \vec{r}_E(t) = R_E(\cos(\omega_E t),\ \sin(\omega_E t))
  $$
- **Mars** orbiting the Sun in a circle of radius $R_M$:
  $$
  \vec{r}_M(t) = R_M(\cos(\omega_M t),\ \sin(\omega_M t))
  $$
- Orbital circles drawn as thin reference rings
- A line connecting Earth and Mars to show their current separation

**Key moments visible in Panel A:**

| Event | Condition | Earth–Mars angle |
|:---|:---|:---:|
| Conjunction | Both on same side | $0°$ |
| Quadrature | Mars $90°$ from Earth | $90°$ |
| Opposition | Opposite sides of Sun | $180°$ |

---

### Panel B — Geocentric view (Mars as seen from Earth)

**What is shown:**

- **Earth fixed** at the center of Panel B
- The **trace of Mars** plotted as:
  $$
  \vec{r}_{M/E}(t) = \bigl(R_M\cos(\omega_M t) - R_E\cos(\omega_E t),\
  R_M\sin(\omega_M t) - R_E\sin(\omega_E t)\bigr)
  $$
- The path traced out over a full synodic period ($\approx 2.135$ years)

**The retrograde loop:**

The most striking feature of Panel B is the **retrograde loop** — a period
when Mars appears to move backward (westward) against the background stars.
This occurs near **opposition**, when Earth passes between the Sun and Mars.

**Why retrograde happens — step by step:**

1. Earth moves faster than Mars ($\omega_E > \omega_M$)
2. As Earth approaches opposition, it overtakes Mars
3. From Earth's perspective, Mars appears to slow down, stop, reverse
   direction, stop again, then resume forward motion
4. This creates a loop or zigzag in the geocentric trajectory

**Approximate angular velocity of Mars as seen from Earth:**

The apparent angular velocity of Mars in the geocentric frame is:

$$
\frac{d}{dt}\!\left[\arctan\!\left(\frac{y_{M/E}}{x_{M/E}}\right)\right]
$$

This is complicated in general, but near opposition it becomes approximately:

$$
\omega_{\text{apparent}} \approx \omega_M - \omega_E < 0
$$

The negative value means Mars moves **backward** (retrograde) near opposition.

**Shape of the geocentric path:**

The path is not a simple circle — it is a complex looping curve called an
**epitrochoid** (a curve traced by a point on a circle rolling around another
circle). Over many synodic periods it fills out a rosette pattern.

> **Explanation:**
> This is one of the most historically important results in all of astronomy.
> Before Copernicus, people could not explain why Mars sometimes appears to
> move backward across the sky. The geocentric (Earth-centered) model required
> complicated "epicycles" to reproduce this behavior. The Copernican
> (Sun-centered) model explains it instantly: retrograde motion is just an
> optical illusion caused by Earth overtaking Mars on the inside lane of the
> solar system, like a faster car on a highway overtaking a slower one — the
> slower car appears to move backward relative to the distant background.
> Panel A shows the true, simple circular motion. Panel B shows what an
> Earth-based observer actually sees — the confusing loops that puzzled
> astronomers for centuries.

---

### Connection between the two panels

The two panels show the **same physical reality** from two different viewpoints:

| | Panel A (Heliocentric) | Panel B (Geocentric) |
|:---|:---:|:---:|
| Center | Sun | Earth |
| Earth's path | Circle of radius $R_E$ | Fixed point |
| Mars's path | Circle of radius $R_M$ | Looping epitrochoid |
| Motion appearance | Simple, orderly | Complex, with retrograde |
| Mathematical description | $\vec{r}_M(t)$, $\vec{r}_E(t)$ separate | $\vec{r}_{M/E}(t) = \vec{r}_M - \vec{r}_E$ |

The transformation between them is simply:

$$
\vec{r}_{M/E}(t) = \vec{r}_M(t) - \vec{r}_E(t)
$$

---

## Possible Questions and Answers

**Q1: What is the synodic period, and how does it differ from the
orbital period?**

A: The **orbital period** (sidereal period) is the time for a planet to
complete one full orbit around the Sun relative to the fixed stars:
$T_E = 1$ year, $T_M = 1.881$ years. The **synodic period** is the time
between successive identical alignments of Earth and Mars as seen from
Earth (e.g., conjunction to conjunction). It is given by:
$$
\frac{1}{T_{\text{syn}}} = \frac{1}{T_E} - \frac{1}{T_M}
\implies T_{\text{syn}} = \frac{T_E T_M}{T_M - T_E} \approx 2.135\ \text{years}
$$
The synodic period is always longer than the difference of the orbital periods
because Earth must "catch up" to Mars after already completing a full orbit.

---

**Q2: Why does Mars appear to move backward (retrograde) as seen from Earth?**

A: Because Earth moves faster than Mars and periodically overtakes it. Near
opposition (when Earth is directly between the Sun and Mars), Earth is
moving faster in the same direction as Mars. From Earth's perspective, Mars
appears to shift backward against the background stars — just as a slower
car on a highway appears to move backward relative to you when you overtake
it. Mathematically, the geocentric angular velocity of Mars becomes negative
near opposition: the angle of $\vec{r}_{M/E}$ temporarily decreases instead
of increasing. This lasts for about $72$ days for Mars.

---

**Q3: At opposition, Mars is closest to Earth. Why is this the best time
to observe Mars?**

A: At opposition, three things coincide: (1) Mars is on the opposite side
of Earth from the Sun, so it rises at sunset and is visible all night;
(2) Mars is at its minimum distance from Earth ($|R_M - R_E| = 0.524$ AU),
so it appears largest and brightest in the sky; (3) the full face of Mars
is illuminated by the Sun as seen from Earth. These factors make opposition
the ideal time for telescopic observation. Not all oppositions are equal —
if opposition occurs when Mars is near perihelion (closest point to the Sun),
the distance can be as small as $0.37$ AU (a "perihelic opposition").

---

**Q4: How does the formula $|\vec{r}_{M/E}| = \sqrt{R_M^2 + R_E^2 - 2R_MR_E\cos\theta}$
relate to the law of cosines?**

A: It is exactly the law of cosines. The Sun, Earth, and Mars form a triangle.
The Sun is at the origin, Earth is at distance $R_E$, Mars is at distance $R_M$,
and the angle at the Sun between them is $\theta = (\omega_M - \omega_E)t$.
The law of cosines for a triangle with sides $a$, $b$ and included angle $C$
states $c^2 = a^2 + b^2 - 2ab\cos C$. Here $a = R_E$, $b = R_M$, $C = \theta$,
and $c = |\vec{r}_{M/E}|$. The formula gives the Earth–Mars distance directly
from the triangle geometry without needing to compute the full vector.

---

**Q5: What would the geocentric trajectory of Mars look like if both planets
had the same orbital period?**

A: If $\omega_E = \omega_M = \omega$ (same period), then:
$$
\vec{r}_{M/E}(t) = \bigl((R_M - R_E)\cos(\omega t),\ (R_M - R_E)\sin(\omega t)\bigr)
$$
This is a **perfect circle** of radius $R_M - R_E$ centered on Earth. Mars
would appear to orbit Earth at a fixed distance, always at the same angular
speed, with no retrograde motion at all. The retrograde loops only appear
because the two planets have different orbital periods — the changing
angular separation is what creates the complex looping path in the
geocentric frame.