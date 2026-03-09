# Problem Set 1 – Problem 6: Curve Length and Numerical Integration

---

## Overview

This problem asks us to find the **arc length** of a parabolic trajectory — the actual distance travelled along the curve, not just the straight-line distance from start to finish. We will:

1. Derive the velocity vector and its magnitude
2. Set up the arc length integral
3. Solve it analytically (it requires a substitution and a known integral formula)
4. Also solve it numerically using the **trapezoidal rule**

> **Key idea:** The arc length of a parametric curve $\vec{r}(t) = (x(t), y(t))$ over $t \in [a, b]$ is:
> $$s = \int_a^b |\vec{v}(t)|\, dt = \int_a^b \sqrt{\dot{x}^2 + \dot{y}^2}\, dt$$
> This formula says: add up all the tiny distances $|\vec{v}(t)|\,dt$ travelled in each infinitesimal time step $dt$. It is the continuous generalisation of "distance = speed × time."

**Given trajectory:**
$$x(t) = t, \qquad y(t) = t^2, \qquad t \in [0, 1]$$

---

## 6.1 – Velocity vector $\vec{v}(t)$

Differentiating each component:

$$\vec{v}(t) = \frac{d\vec{r}}{dt} = \left(\frac{d}{dt}(t),\ \frac{d}{dt}(t^2)\right) = (1,\ 2t)$$

$$\boxed{\vec{v}(t) = (1,\ 2t)}$$

> **Explanation:** This is the same parabola from Problem 4, Curve C. The velocity has a constant horizontal component of $1$ (the object always moves right at the same rate) and a vertical component $2t$ that grows linearly (the object moves upward faster and faster). The trajectory is the parabola $y = x^2$.

---

## 6.2 – Magnitude of velocity $|\vec{v}(t)|$

$$|\vec{v}(t)| = \sqrt{1^2 + (2t)^2} = \sqrt{1 + 4t^2}$$

$$\boxed{|\vec{v}(t)| = \sqrt{1 + 4t^2}}$$

> **Explanation:** The speed grows with $t$ — the object moves faster as it travels further along the parabola. At $t = 0$ the speed is $1$; at $t = 1$ the speed is $\sqrt{5} \approx 2.236$. The total arc length is the integral of this speed over time.

---

## 6.3 – Arc length integral

$$s = \int_0^1 |\vec{v}(t)|\, dt = \int_0^1 \sqrt{1 + 4t^2}\, dt$$

$$\boxed{s = \int_0^1 \sqrt{1 + 4t^2}\, dt}$$

> **Explanation:** This integral cannot be simplified by inspection — $\sqrt{1 + 4t^2}$ has no elementary antiderivative in its current form. We need a substitution to reduce it to a standard form. However, before doing so analytically, let us note that this is a well-posed integral over a finite interval with a smooth, positive integrand — so both analytical and numerical methods will work.

---

## 6.4 – Analytical evaluation

We use the standard integral formula (derived via trigonometric or hyperbolic substitution):

$$\int \sqrt{1 + u^2}\, du = \frac{u\sqrt{1+u^2}}{2} + \frac{1}{2}\ln\!\left(u + \sqrt{1+u^2}\right) + C$$

**Step 1 — Substitution to match the standard form:**

Let $u = 2t$, so $du = 2\, dt$, i.e. $dt = \frac{du}{2}$.

When $t = 0$: $u = 0$. When $t = 1$: $u = 2$.

$$\int_0^1 \sqrt{1 + 4t^2}\, dt = \int_0^2 \sqrt{1 + u^2}\cdot \frac{du}{2} = \frac{1}{2}\int_0^2 \sqrt{1+u^2}\, du$$

**Step 2 — Apply the standard formula:**

$$\frac{1}{2}\int_0^2 \sqrt{1+u^2}\, du = \frac{1}{2}\left[\frac{u\sqrt{1+u^2}}{2} + \frac{1}{2}\ln\!\left(u + \sqrt{1+u^2}\right)\right]_0^2$$

**Step 3 — Evaluate at $u = 2$:**

$$\frac{u\sqrt{1+u^2}}{2}\bigg|_{u=2} = \frac{2\sqrt{1+4}}{2} = \frac{2\sqrt{5}}{2} = \sqrt{5}$$

$$\frac{1}{2}\ln\!\left(u + \sqrt{1+u^2}\right)\bigg|_{u=2} = \frac{1}{2}\ln\!\left(2 + \sqrt{5}\right)$$

**Step 4 — Evaluate at $u = 0$:**

$$\frac{u\sqrt{1+u^2}}{2}\bigg|_{u=0} = \frac{0 \cdot 1}{2} = 0$$

$$\frac{1}{2}\ln\!\left(u + \sqrt{1+u^2}\right)\bigg|_{u=0} = \frac{1}{2}\ln(0 + 1) = \frac{1}{2}\ln 1 = 0$$

**Step 5 — Combine:**

$$s = \frac{1}{2}\left[\left(\sqrt{5} + \frac{1}{2}\ln(2+\sqrt{5})\right) - (0 + 0)\right]$$

$$= \frac{1}{2}\left(\sqrt{5} + \frac{1}{2}\ln(2+\sqrt{5})\right)$$

$$= \frac{\sqrt{5}}{2} + \frac{1}{4}\ln(2+\sqrt{5})$$

**Numerical evaluation:**

- $\sqrt{5} \approx 2.2361$, so $\frac{\sqrt{5}}{2} \approx 1.1180$
- $2 + \sqrt{5} \approx 4.2361$, so $\ln(4.2361) \approx 1.4436$, thus $\frac{1}{4}\ln(2+\sqrt{5}) \approx 0.3609$

$$\boxed{s = \frac{\sqrt{5}}{2} + \frac{1}{4}\ln(2+\sqrt{5}) \approx 1.4789}$$

> **Explanation:** The substitution $u = 2t$ was needed to turn $\sqrt{1 + 4t^2}$ into the standard form $\sqrt{1 + u^2}$. The standard integral itself is derived by the substitution $u = \sinh\theta$ (hyperbolic sine), which converts $\sqrt{1 + u^2}$ into $\cosh\theta$ — a much easier function to integrate. The appearance of $\ln(2 + \sqrt{5})$ is not a coincidence: it equals $\sinh^{-1}(2) = \text{arcsinh}(2)$, the inverse hyperbolic sine of $2$.

---

## 6.5 – Trapezoidal rule implementation in HTML/JS

### What is the trapezoidal rule?

The **trapezoidal rule** approximates a definite integral by dividing the interval into $N$ equal subintervals and approximating the area under the curve in each subinterval with a **trapezoid** (instead of a rectangle). The formula is:

$$\int_a^b f(t)\, dt \approx \frac{h}{2}\left[f(t_0) + 2f(t_1) + 2f(t_2) + \cdots + 2f(t_{N-1}) + f(t_N)\right]$$

where $h = \frac{b-a}{N}$ is the width of each subinterval and $t_i = a + i\cdot h$.

The **error** of the trapezoidal rule decreases as $O(h^2) = O(1/N^2)$ — doubling $N$ reduces the error by a factor of 4.

> **Explanation:** Think of the trapezoidal rule as drawing $N$ thin trapezoids under the curve and summing their areas. Each trapezoid has parallel sides of heights $f(t_i)$ and $f(t_{i+1})$ and width $h$, giving area $\frac{h}{2}(f(t_i) + f(t_{i+1}))$. Summing these telescopes into the formula above. As $N \to \infty$, the trapezoids become thinner and their total area converges to the exact integral.

---

### HTML/JS Implementation

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Problem 6 – Arc Length & Trapezoidal Rule</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 900px;
      margin: 40px auto;
      padding: 0 20px;
      background: #f8f9fa;
      color: #222;
    }
    h2 { color: #2c3e50; }
    .panel {
      background: white;
      border-radius: 8px;
      padding: 20px;
      margin-bottom: 24px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.08);
    }
    canvas { display: block; margin: 0 auto; }
    label { font-weight: bold; }
    input[type=range] { width: 300px; vertical-align: middle; }
    .result {
      font-size: 1.1em;
      margin-top: 12px;
      background: #eaf4fb;
      padding: 10px 16px;
      border-radius: 6px;
    }
    table {
      border-collapse: collapse;
      width: 100%;
      margin-top: 12px;
      font-size: 0.92em;
    }
    th, td {
      border: 1px solid #ccc;
      padding: 6px 12px;
      text-align: right;
    }
    th { background: #2c3e50; color: white; }
    tr:nth-child(even) { background: #f2f2f2; }
  </style>
</head>
<body>

<h2>Problem 6 – Arc Length of y = x² and Trapezoidal Rule</h2>

<!-- TRAJECTORY CANVAS -->
<div class="panel">
  <h3>Trajectory: x(t) = t, y(t) = t², t ∈ [0,1]</h3>
  <canvas id="trajCanvas" width="500" height="400"></canvas>
</div>

<!-- TRAPEZOIDAL RULE CONTROL -->
<div class="panel">
  <h3>Trapezoidal Rule Approximation</h3>
  <label for="nSlider">Number of divisions N = <span id="nVal">10</span></label><br><br>
  <input type="range" id="nSlider" min="1" max="200" value="10"
         oninput="document.getElementById('nVal').textContent=this.value; update()">
  <div class="result" id="resultBox"></div>
</div>

<!-- CONVERGENCE TABLE -->
<div class="panel">
  <h3>Convergence Table</h3>
  <table id="convTable">
    <thead>
      <tr>
        <th>N</th>
        <th>Approx. s</th>
        <th>Error |s − s_exact|</th>
        <th>Error / (1/N²)</th>
      </tr>
    </thead>
    <tbody id="convBody"></tbody>
  </table>
</div>

<!-- ERROR PLOT CANVAS -->
<div class="panel">
  <h3>Error vs N (log-log scale)</h3>
  <canvas id="errCanvas" width="600" height="320"></canvas>
  <p style="text-align:center; color:#555; font-size:0.9em">
    Slope ≈ −2 on log-log scale confirms O(1/N²) convergence
  </p>
</div>

<script>
  // ── Exact answer ──────────────────────────────────────────────
  const EXACT = Math.sqrt(5)/2 + Math.log(2 + Math.sqrt(5))/4;

  // ── Integrand: speed |v(t)| = sqrt(1 + 4t²) ──────────────────
  function speed(t) { return Math.sqrt(1 + 4*t*t); }

  // ── Trapezoidal rule on [0,1] with N subintervals ─────────────
  function trapezoid(N) {
    const h = 1 / N;
    let sum = speed(0) + speed(1);
    for (let i = 1; i < N; i++) sum += 2 * speed(i * h);
    return (h / 2) * sum;
  }

  // ── Draw trajectory ───────────────────────────────────────────
  function drawTrajectory() {
    const canvas = document.getElementById('trajCanvas');
    const ctx = canvas.getContext('2d');
    const W = canvas.width, H = canvas.height;
    const pad = 60;
    ctx.clearRect(0, 0, W, H);

    // coordinate transform: t∈[0,1] → x∈[0,1], y∈[0,1]
    function px(x) { return pad + x * (W - 2*pad); }
    function py(y) { return H - pad - y * (H - 2*pad); }

    // axes
    ctx.strokeStyle = '#aaa'; ctx.lineWidth = 1;
    ctx.beginPath();
    ctx.moveTo(pad, pad); ctx.lineTo(pad, H-pad);
    ctx.lineTo(W-pad, H-pad);
    ctx.stroke();

    // axis labels
    ctx.fillStyle = '#555'; ctx.font = '13px Arial';
    ctx.fillText('x', W-pad+8, H-pad+4);
    ctx.fillText('y', pad-18, pad-8);
    for (let v of [0, 0.25, 0.5, 0.75, 1.0]) {
      ctx.fillText(v.toFixed(2), px(v)-14, H-pad+18);
      ctx.fillText(v.toFixed(2), pad-42, py(v)+4);
    }

    // parabola
    ctx.strokeStyle = '#2980b9'; ctx.lineWidth = 2.5;
    ctx.beginPath();
    for (let i = 0; i <= 200; i++) {
      const t = i / 200;
      i === 0 ? ctx.moveTo(px(t), py(t*t)) : ctx.lineTo(px(t), py(t*t));
    }
    ctx.stroke();

    // velocity arrow at t=0.5
    const t0 = 0.5;
    const vx = 1, vy = 2*t0;
    const scale = 0.12;
    ctx.strokeStyle = '#e74c3c'; ctx.lineWidth = 2;
    ctx.beginPath();
    ctx.moveTo(px(t0), py(t0*t0));
    ctx.lineTo(px(t0 + vx*scale), py(t0*t0 + vy*scale));
    ctx.stroke();
    ctx.fillStyle = '#e74c3c';
    ctx.fillText('v(0.5)', px(t0 + vx*scale)+4, py(t0*t0 + vy*scale)-4);

    // start/end points
    ctx.fillStyle = '#27ae60';
    ctx.beginPath(); ctx.arc(px(0), py(0), 5, 0, 2*Math.PI); ctx.fill();
    ctx.fillText('t=0', px(0)+8, py(0)-6);

    ctx.fillStyle = '#8e44ad';
    ctx.beginPath(); ctx.arc(px(1), py(1), 5, 0, 2*Math.PI); ctx.fill();
    ctx.fillText('t=1', px(1)+6, py(1)-6);

    // title
    ctx.fillStyle = '#2c3e50'; ctx.font = 'bold 14px Arial';
    ctx.fillText('y = x²  (parabola, t ∈ [0,1])', pad, pad-20);
  }

  // ── Update result box ─────────────────────────────────────────
  function update() {
    const N = parseInt(document.getElementById('nSlider').value);
    const approx = trapezoid(N);
    const err = Math.abs(approx - EXACT);
    document.getElementById('resultBox').innerHTML =
      `<b>N = ${N}</b><br>` +
      `Trapezoidal approximation: <b>s ≈ ${approx.toFixed(8)}</b><br>` +
      `Exact value: s = ${EXACT.toFixed(8)}<br>` +
      `Error: ${err.toExponential(4)}`;
    drawErrorPlot();
  }

  // ── Build convergence table ───────────────────────────────────
  function buildTable() {
    const Nvals = [1, 2, 5, 10, 20, 50, 100, 200];
    const tbody = document.getElementById('convBody');
    tbody.innerHTML = '';
    for (const N of Nvals) {
      const approx = trapezoid(N);
      const err = Math.abs(approx - EXACT);
      const ratio = err * N * N;
      const tr = document.createElement('tr');
      tr.innerHTML =
        `<td>${N}</td>` +
        `<td>${approx.toFixed(8)}</td>` +
        `<td>${err.toExponential(4)}</td>` +
        `<td>${ratio.toFixed(5)}</td>`;
      tbody.appendChild(tr);
    }
  }

  // ── Error vs N log-log plot ───────────────────────────────────
  function drawErrorPlot() {
    const canvas = document.getElementById('errCanvas');
    const ctx = canvas.getContext('2d');
    const W = canvas.width, H = canvas.height;
    const pad = 60;
    ctx.clearRect(0, 0, W, H);

    const Nvals = [];
    for (let n = 1; n <= 200; n++) Nvals.push(n);
    const errors = Nvals.map(n => Math.abs(trapezoid(n) - EXACT));

    const logN = Nvals.map(n => Math.log10(n));
    const logE = errors.map(e => e > 0 ? Math.log10(e) : -12);

    const minLN = 0, maxLN = Math.log10(200);
    const minLE = Math.min(...logE.filter(v => isFinite(v))) - 0.3;
    const maxLE = Math.max(...logE.filter(v => isFinite(v))) + 0.3;

    function px(lx) { return pad + (lx - minLN) / (maxLN - minLN) * (W - 2*pad); }
    function py(ly) { return H - pad - (ly - minLE) / (maxLE - minLE) * (H - 2*pad); }

    // axes
    ctx.strokeStyle = '#aaa'; ctx.lineWidth = 1;
    ctx.beginPath();
    ctx.moveTo(pad, pad); ctx.lineTo(pad, H-pad); ctx.lineTo(W-pad, H-pad);
    ctx.stroke();

    // axis labels
    ctx.fillStyle = '#555'; ctx.font = '12px Arial';
    ctx.fillText('log₁₀(N)', W/2 - 20, H-10);
    ctx.save(); ctx.translate(16, H/2); ctx.rotate(-Math.PI/2);
    ctx.fillText('log₁₀(error)', -40, 0); ctx.restore();

    for (let lx = 0; lx <= 2.4; lx += 0.5) {
      ctx.fillText(lx.toFixed(1), px(lx)-8, H-pad+16);
    }
    for (let ly = Math.ceil(minLE); ly <= Math.floor(maxLE); ly++) {
      ctx.fillText(ly, pad-32, py(ly)+4);
    }

    // reference slope -2 line
    ctx.strokeStyle = '#e74c3c'; ctx.lineWidth = 1.5;
    ctx.setLineDash([6, 4]);
    const refX1 = 0.5, refX2 = 2.2;
    const refY1 = maxLE - 0.5;
    const refY2 = refY1 - 2*(refX2 - refX1);
    ctx.beginPath();
    ctx.moveTo(px(refX1), py(refY1));
    ctx.lineTo(px(refX2), py(refY2));
    ctx.stroke();
    ctx.setLineDash([]);
    ctx.fillStyle = '#e74c3c';
    ctx.fillText('slope = −2', px(refX2)+6, py(refY2)+4);

    // error curve
    ctx.strokeStyle = '#2980b9'; ctx.lineWidth = 2;
    ctx.beginPath();
    let started = false;
    for (let i = 0; i < Nvals.length; i++) {
      if (!isFinite(logE[i])) continue;
      if (!started) { ctx.moveTo(px(logN[i]), py(logE[i])); started = true; }
      else ctx.lineTo(px(logN[i]), py(logE[i]));
    }
    ctx.stroke();

    // current N marker
    const N = parseInt(document.getElementById('nSlider').value);
    const curLogN = Math.log10(N);
    const curLogE = Math.log10(Math.abs(trapezoid(N) - EXACT));
    if (isFinite(curLogE)) {
      ctx.fillStyle = '#e67e22';
      ctx.beginPath();
      ctx.arc(px(curLogN), py(curLogE), 6, 0, 2*Math.PI);
      ctx.fill();
      ctx.fillStyle = '#e67e22';
      ctx.font = 'bold 12px Arial';
      ctx.fillText(`N=${N}`, px(curLogN)+8, py(curLogE)-6);
    }

    ctx.fillStyle = '#2c3e50'; ctx.font = 'bold 13px Arial';
    ctx.fillText('Error convergence (log-log)', pad, pad-18);
  }

  // ── Initialise ────────────────────────────────────────────────
  drawTrajectory();
  buildTable();
  update();
</script>
</body>
</html>
```

> **How to use the application:**
> - The top panel shows the parabolic trajectory $y = x^2$ with the velocity vector drawn at $t = 0.5$.
> - The slider controls $N$ — drag it right to increase the number of trapezoids.
> - The result box shows the numerical approximation, the exact value, and the current error.
> - The convergence table shows the error for fixed values of $N = 1, 2, 5, 10, 20, 50, 100, 200$.
> - The error plot shows error vs $N$ on a **log-log scale** — the slope of $-2$ confirms the trapezoidal rule converges as $O(1/N^2)$.

---

## Summary

| Step | Result |
|---|---|
| Velocity vector | $\vec{v}(t) = (1,\ 2t)$ |
| Speed | $\|\vec{v}(t)\| = \sqrt{1 + 4t^2}$ |
| Arc length integral | $s = \displaystyle\int_0^1 \sqrt{1 + 4t^2}\, dt$ |
| Substitution used | $u = 2t$, reducing to $\frac{1}{2}\int_0^2\sqrt{1+u^2}\,du$ |
| Exact analytical result | $s = \dfrac{\sqrt{5}}{2} + \dfrac{1}{4}\ln(2+\sqrt{5}) \approx 1.4789$ |
| Trapezoidal rule error | $O(1/N^2)$ — halving $h$ reduces error by factor 4 |

---

## 5 Possible Questions & Answers

---

**Q1: Why can't we just compute the straight-line distance from $(0, 0)$ to $(1, 1)$ instead of integrating?**

**A:** The straight-line (Euclidean) distance from $(0,0)$ to $(1,1)$ is $\sqrt{1^2 + 1^2} = \sqrt{2} \approx 1.414$. But this ignores the fact that the object does *not* travel in a straight line — it follows the curved parabola $y = x^2$. The arc length $s \approx 1.479$ is larger than $\sqrt{2}$ because the actual path is longer than the shortcut. The integral $\int |\vec{v}|\,dt$ sums up infinitely many tiny straight-line segments along the curve, capturing the total path length correctly.

---

**Q2: Why does the substitution $u = 2t$ simplify the integral? What is the general strategy?**

**A:** The integrand $\sqrt{1 + 4t^2}$ does not match any standard form directly, but $\sqrt{1 + u^2}$ does — it is a known integral solved by hyperbolic substitution $u = \sinh\theta$. The substitution $u = 2t$ transforms the coefficient of $t^2$ from $4$ to $1$, making the exponent match the standard form. The general strategy for arc length integrals is: (1) identify the form of the integrand, (2) use an algebraic substitution to reduce it to a standard form, (3) apply the known formula. For more complex curves, no closed form may exist and numerical methods become essential.

---

**Q3: What is the order of convergence of the trapezoidal rule, and what does it mean practically?**

**A:** The trapezoidal rule has **second-order convergence**: the error scales as $O(h^2) = O(1/N^2)$. This means if you double $N$ (halve $h$), the error decreases by a factor of $4$. For example, from the convergence table: at $N = 10$ the error is roughly $10^{-3}$, and at $N = 100$ it is roughly $10^{-5}$ — a reduction by $100 = 10^2$, consistent with $O(1/N^2)$. On a log-log plot of error vs $N$, this appears as a straight line with slope $-2$. In practice, second-order convergence is decent but not spectacular — higher-order methods like Simpson's rule ($O(h^4)$) or Gaussian quadrature converge much faster.

---

**Q4: The arc length integral involves $\ln(2 + \sqrt{5})$. Is this related to inverse hyperbolic functions?**

**A:** Yes — this is not a coincidence. The standard integral $\int_0^u \sqrt{1+s^2}\,ds$ produces $\sinh^{-1}(u) = \ln(u + \sqrt{1+u^2})$ as part of its result. At the upper limit $u = 2$: $\sinh^{-1}(2) = \ln(2 + \sqrt{4+1}) = \ln(2 + \sqrt{5})$. The appearance of the natural logarithm here is a direct consequence of the hyperbolic substitution used to evaluate the integral. This is one of many places in mathematics where arc length computations naturally produce inverse hyperbolic or logarithmic expressions, even for simple polynomial curves.

---

**Q5: Why is it important to plot the error on a log-log scale rather than a linear scale?**

**A:** On a **linear scale**, the error curve for large $N$ is essentially flat near zero and uninformative — it is very hard to distinguish between $O(1/N)$, $O(1/N^2)$, and $O(1/N^3)$ convergence visually. On a **log-log scale**, a power-law relationship $\text{error} \propto N^{-p}$ appears as a straight line with slope $-p$. This makes it trivial to read off the convergence order: a slope of $-2$ confirms $O(1/N^2)$, a slope of $-4$ would confirm Simpson's rule ($O(1/N^4)$), etc. Log-log plots are the standard tool in numerical analysis for diagnosing and verifying convergence rates of algorithms.