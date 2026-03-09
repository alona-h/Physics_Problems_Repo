# Problem Set 1 – Problem 7: Work of a Force Along a Trajectory

---

## Overview

This problem introduces the **line integral** — one of the most important concepts in physics and engineering. A line integral computes the cumulative effect of a force acting on an object as it moves along a curved path. The result is the **work** done by the force.

> **Key idea:** Work is not just force times distance. When the force changes direction and magnitude along a curved path, we must integrate:
> $$W = \int_C \vec{F} \cdot d\vec{r} = \int_a^b \vec{F}(\vec{r}(t)) \cdot \vec{v}(t)\, dt$$
> At each instant, only the component of force **parallel to the motion** does work. The dot product $\vec{F} \cdot \vec{v}$ extracts exactly that component, and integrating it over time gives the total work.

**Given:**
$$\vec{F}(x, y) = (y,\ 2x), \qquad x = t,\quad y = t^2, \qquad t \in [0, 1]$$

---

## 7.1 – Velocity vector $\vec{v}(t)$

Differentiating the parametric trajectory $(x(t), y(t)) = (t, t^2)$:

$$\vec{v}(t) = \frac{d}{dt}(t,\ t^2) = (1,\ 2t)$$

$$\boxed{\vec{v}(t) = (1,\ 2t)}$$

This is identical to Problem 6 — the same parabolic trajectory.

> **Explanation:** The velocity vector tells us the direction and speed of motion at each point along the path. We need it because the work integral requires us to know how the object is moving at every instant — specifically, how the force aligns with that motion.

---

## 7.2 – Work done by the force: analytical calculation

### Step 1 — Express $\vec{F}$ along the trajectory

The force $\vec{F}(x, y) = (y, 2x)$ is given in terms of $x$ and $y$. We substitute the parametric equations $x = t$, $y = t^2$ to express the force as a function of $t$:

$$\vec{F}(t) = \vec{F}(x(t),\ y(t)) = (y(t),\ 2x(t)) = (t^2,\ 2t)$$

### Step 2 — Set up the line integral

$$W = \int_C \vec{F} \cdot d\vec{r} = \int_0^1 \vec{F}(t) \cdot \vec{v}(t)\, dt$$

Compute the dot product $\vec{F}(t) \cdot \vec{v}(t)$:

$$\vec{F}(t) \cdot \vec{v}(t) = (t^2,\ 2t) \cdot (1,\ 2t)$$

$$= t^2 \cdot 1 + 2t \cdot 2t$$

$$= t^2 + 4t^2$$

$$= 5t^2$$

### Step 3 — Evaluate the integral

$$W = \int_0^1 5t^2\, dt$$

$$= 5 \int_0^1 t^2\, dt$$

$$= 5 \left[\frac{t^3}{3}\right]_0^1$$

$$= 5 \cdot \left(\frac{1^3}{3} - \frac{0^3}{3}\right)$$

$$= 5 \cdot \frac{1}{3}$$

$$\boxed{W = \frac{5}{3} \approx 1.6\overline{6}}$$

> **Explanation:** The dot product $\vec{F} \cdot \vec{v}$ gives the instantaneous power — the rate at which the force does work at each moment. Integrating this over time gives the total work. The result $W = 5/3$ is positive, meaning the force overall acts in the same general direction as the motion — it adds energy to the object. If $W$ were negative, the force would be opposing the motion (like friction), and if $W = 0$, the force would be everywhere perpendicular to the path (like the normal force on a surface).

---

## 7.3 – Riemann sum interpretation and numerical calculation in HTML/JS

### Riemann sum interpretation

The work integral can be written as the limit of a Riemann sum. Dividing $[0, 1]$ into $N$ equal subintervals of width $h = 1/N$, with sample points $t_i = i \cdot h$:

$$W = \int_0^1 \vec{F}(t) \cdot \vec{v}(t)\, dt = \lim_{N \to \infty} \sum_{i=0}^{N-1} \left[\vec{F}(t_i) \cdot \vec{v}(t_i)\right] \cdot h$$

$$= \lim_{N \to \infty} \sum_{i=0}^{N-1} 5t_i^2 \cdot h$$

Each term $[\vec{F}(t_i) \cdot \vec{v}(t_i)] \cdot h$ represents the approximate work done over the small time interval $[t_i, t_{i+1}]$: the force is treated as constant over that tiny segment, and $h$ is the duration. As $N \to \infty$ and $h \to 0$, this sum converges to the exact integral $5/3$.

> **Explanation:** The Riemann sum is the finite, computable approximation to the integral. Think of it as: at each of the $N$ sample times, you measure the force on the object and the direction it's moving, compute how much work is done in that tiny time slice, and add them all up. As you use more and more time slices (larger $N$), the approximation gets closer and closer to the true value. This is exactly what numerical integration does in a computer.

---

### HTML/JS Implementation

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <title>Problem 7 – Work of a Force</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 920px;
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
    input[type=range] { width: 320px; vertical-align: middle; }
    .result {
      font-size: 1.05em;
      margin-top: 14px;
      background: #eaf4fb;
      padding: 10px 16px;
      border-radius: 6px;
      line-height: 1.8;
    }
    table {
      border-collapse: collapse;
      width: 100%;
      margin-top: 12px;
      font-size: 0.91em;
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

<h2>Problem 7 – Work of F = (y, 2x) Along y = x²</h2>

<!-- TRAJECTORY + FORCE FIELD CANVAS -->
<div class="panel">
  <h3>Trajectory and Force Field</h3>
  <canvas id="trajCanvas" width="560" height="400"></canvas>
  <p style="text-align:center; color:#666; font-size:0.9em">
    Blue curve: trajectory &nbsp;|&nbsp;
    Red arrows: force <b>F</b>(x,y) = (y, 2x) at sample points
  </p>
</div>

<!-- RIEMANN SUM CONTROL -->
<div class="panel">
  <h3>Riemann Sum Approximation of Work</h3>
  <label><b>Number of subintervals N = <span id="nVal">10</span></b></label><br><br>
  <input type="range" id="nSlider" min="1" max="500" value="10"
         oninput="document.getElementById('nVal').textContent=this.value; update()">
  <div class="result" id="resultBox"></div>
</div>

<!-- CONVERGENCE TABLE -->
<div class="panel">
  <h3>Convergence Table</h3>
  <table>
    <thead>
      <tr>
        <th>N</th>
        <th>Riemann sum W</th>
        <th>Error |W − 5/3|</th>
        <th>Error × N</th>
      </tr>
    </thead>
    <tbody id="convBody"></tbody>
  </table>
</div>

<!-- ERROR PLOT -->
<div class="panel">
  <h3>Error vs N (log-log scale)</h3>
  <canvas id="errCanvas" width="600" height="320"></canvas>
  <p style="text-align:center; color:#555; font-size:0.9em">
    Slope ≈ −1 confirms O(1/N) convergence for the left-endpoint Riemann sum
  </p>
</div>

<script>
  const EXACT = 5 / 3;

  // Integrand: F(t)·v(t) = 5t²
  function integrand(t) {
    const Fx = t * t;   // y(t) = t²
    const Fy = 2 * t;   // 2x(t) = 2t
    const vx = 1;
    const vy = 2 * t;
    return Fx * vx + Fy * vy; // = t² + 4t² = 5t²
  }

  // Left-endpoint Riemann sum
  function riemannSum(N) {
    const h = 1 / N;
    let sum = 0;
    for (let i = 0; i < N; i++) sum += integrand(i * h) * h;
    return sum;
  }

  // ── Draw trajectory and force vectors ──────────────────────────
  function drawTrajectory() {
    const canvas = document.getElementById('trajCanvas');
    const ctx = canvas.getContext('2d');
    const W = canvas.width, H = canvas.height;
    const pad = 65;

    ctx.clearRect(0, 0, W, H);

    function px(x) { return pad + x * (W - 2 * pad); }
    function py(y) { return H - pad - y * (H - 2 * pad); }

    // Grid
    ctx.strokeStyle = '#e8e8e8'; ctx.lineWidth = 1;
    for (let v = 0; v <= 1; v += 0.25) {
      ctx.beginPath(); ctx.moveTo(px(v), py(0)); ctx.lineTo(px(v), py(1)); ctx.stroke();
      ctx.beginPath(); ctx.moveTo(px(0), py(v)); ctx.lineTo(px(1), py(v)); ctx.stroke();
    }

    // Axes
    ctx.strokeStyle = '#999'; ctx.lineWidth = 1.5;
    ctx.beginPath(); ctx.moveTo(pad, pad); ctx.lineTo(pad, H - pad);
    ctx.lineTo(W - pad, H - pad); ctx.stroke();

    // Axis labels
    ctx.fillStyle = '#555'; ctx.font = '12px Arial';
    for (let v = 0; v <= 1; v += 0.25) {
      ctx.fillText(v.toFixed(2), px(v) - 10, H - pad + 18);
      ctx.fillText(v.toFixed(2), pad - 44, py(v) + 4);
    }
    ctx.fillStyle = '#2c3e50'; ctx.font = '13px Arial';
    ctx.fillText('x', W - pad + 10, H - pad + 4);
    ctx.fillText('y', pad - 20, pad - 10);

    // Parabola trajectory
    ctx.strokeStyle = '#2980b9'; ctx.lineWidth = 2.5;
    ctx.beginPath();
    for (let i = 0; i <= 300; i++) {
      const t = i / 300;
      i === 0 ? ctx.moveTo(px(t), py(t * t)) : ctx.lineTo(px(t), py(t * t));
    }
    ctx.stroke();

    // Direction arrow along trajectory at t=0.7
    const ta = 0.7, sc = 0.07;
    ctx.strokeStyle = '#2980b9'; ctx.lineWidth = 1.5;
    const vxA = 1, vyA = 2 * ta;
    const len = Math.sqrt(vxA * vxA + vyA * vyA);
    drawArrow(ctx, px(ta), py(ta * ta),
      px(ta + vxA / len * sc), py(ta * ta + vyA / len * sc),
      '#2980b9', 2);

    // Force vectors at sample points
    const samples = [0.1, 0.3, 0.5, 0.7, 0.9];
    const fsc = 0.13;
    for (const t of samples) {
      const Fx = t * t, Fy = 2 * t;
      const flen = Math.sqrt(Fx * Fx + Fy * Fy);
      const x0 = px(t), y0 = py(t * t);
      const x1 = px(t + (Fx / flen) * fsc);
      const y1 = py(t * t + (Fy / flen) * fsc);
      drawArrow(ctx, x0, y0, x1, y1, '#e74c3c', 1.8);
    }

    // Start/end points
    ctx.fillStyle = '#27ae60';
    ctx.beginPath(); ctx.arc(px(0), py(0), 5, 0, 2 * Math.PI); ctx.fill();
    ctx.fillStyle = '#333'; ctx.font = '12px Arial';
    ctx.fillText('(0,0) t=0', px(0) + 8, py(0) + 14);

    ctx.fillStyle = '#8e44ad';
    ctx.beginPath(); ctx.arc(px(1), py(1), 5, 0, 2 * Math.PI); ctx.fill();
    ctx.fillText('(1,1) t=1', px(1) - 55, py(1) - 8);

    // Legend
    ctx.fillStyle = '#2c3e50'; ctx.font = 'bold 13px Arial';
    ctx.fillText('Trajectory: y = x²', pad + 10, pad - 20);
  }

  function drawArrow(ctx, x1, y1, x2, y2, color, lw) {
    const dx = x2 - x1, dy = y2 - y1;
    const angle = Math.atan2(dy, dx);
    const hs = 8;
    ctx.strokeStyle = color; ctx.fillStyle = color; ctx.lineWidth = lw;
    ctx.beginPath(); ctx.moveTo(x1, y1); ctx.lineTo(x2, y2); ctx.stroke();
    ctx.beginPath();
    ctx.moveTo(x2, y2);
    ctx.lineTo(x2 - hs * Math.cos(angle - Math.PI / 7),
               y2 - hs * Math.sin(angle - Math.PI / 7));
    ctx.lineTo(x2 - hs * Math.cos(angle + Math.PI / 7),
               y2 - hs * Math.sin(angle + Math.PI / 7));
    ctx.closePath(); ctx.fill();
  }

  // ── Update result box ──────────────────────────────────────────
  function update() {
    const N = parseInt(document.getElementById('nSlider').value);
    const W = riemannSum(N);
    const err = Math.abs(W - EXACT);
    document.getElementById('resultBox').innerHTML =
      `<b>N = ${N}</b><br>` +
      `Riemann sum (left-endpoint): <b>W ≈ ${W.toFixed(8)}</b><br>` +
      `Exact value (analytical): W = 5/3 = ${EXACT.toFixed(8)}<br>` +
      `Absolute error: ${err.toExponential(4)}<br>` +
      `Relative error: ${(err / EXACT * 100).toFixed(4)}%`;
    drawErrorPlot();
  }

  // ── Convergence table ──────────────────────────────────────────
  function buildTable() {
    const Nvals = [1, 2, 5, 10, 20, 50, 100, 200, 500];
    const tbody = document.getElementById('convBody');
    tbody.innerHTML = '';
    for (const N of Nvals) {
      const W = riemannSum(N);
      const err = Math.abs(W - EXACT);
      const tr = document.createElement('tr');
      tr.innerHTML =
        `<td>${N}</td>` +
        `<td>${W.toFixed(8)}</td>` +
        `<td>${err.toExponential(4)}</td>` +
        `<td>${(err * N).toFixed(5)}</td>`;
      tbody.appendChild(tr);
    }
  }

  // ── Error vs N log-log plot ────────────────────────────────────
  function drawErrorPlot() {
    const canvas = document.getElementById('errCanvas');
    const ctx = canvas.getContext('2d');
    const W = canvas.width, H = canvas.height;
    const pad = 60;
    ctx.clearRect(0, 0, W, H);

    const Nvals = [];
    for (let n = 1; n <= 500; n++) Nvals.push(n);
    const errors = Nvals.map(n => Math.abs(riemannSum(n) - EXACT));

    const logN = Nvals.map(n => Math.log10(n));
    const logE = errors.map(e => e > 1e-14 ? Math.log10(e) : -14);

    const minLN = 0, maxLN = Math.log10(500);
    const finiteE = logE.filter(v => isFinite(v) && v > -13);
    const minLE = Math.min(...finiteE) - 0.3;
    const maxLE = Math.max(...finiteE) + 0.3;

    function pxF(lx) { return pad + (lx - minLN) / (maxLN - minLN) * (W - 2 * pad); }
    function pyF(ly) { return H - pad - (ly - minLE) / (maxLE - minLE) * (H - 2 * pad); }

    // Axes
    ctx.strokeStyle = '#aaa'; ctx.lineWidth = 1;
    ctx.beginPath();
    ctx.moveTo(pad, pad); ctx.lineTo(pad, H - pad);
    ctx.lineTo(W - pad, H - pad); ctx.stroke();

    // Labels
    ctx.fillStyle = '#555'; ctx.font = '12px Arial';
    ctx.fillText('log\u2081\u2080(N)', W / 2 - 20, H - 10);
    ctx.save(); ctx.translate(16, H / 2); ctx.rotate(-Math.PI / 2);
    ctx.fillText('log\u2081\u2080(error)', -40, 0); ctx.restore();

    for (let lx = 0; lx <= Math.log10(500); lx += 0.5) {
      ctx.fillText(lx.toFixed(1), pxF(lx) - 8, H - pad + 16);
    }
    for (let ly = Math.ceil(minLE); ly <= Math.floor(maxLE); ly++) {
      ctx.fillText(ly, pad - 32, pyF(ly) + 4);
    }

    // Reference slope -1
    ctx.strokeStyle = '#e74c3c'; ctx.lineWidth = 1.5; ctx.setLineDash([6, 4]);
    const rx1 = 0.3, rx2 = 2.5;
    const ry1 = maxLE - 0.4;
    const ry2 = ry1 - 1 * (rx2 - rx1);
    ctx.beginPath(); ctx.moveTo(pxF(rx1), pyF(ry1)); ctx.lineTo(pxF(rx2), pyF(ry2));
    ctx.stroke(); ctx.setLineDash([]);
    ctx.fillStyle = '#e74c3c'; ctx.font = '12px Arial';
    ctx.fillText('slope = \u22121', pxF(rx2) + 6, pyF(ry2) + 4);

    // Error curve
    ctx.strokeStyle = '#2980b9'; ctx.lineWidth = 2;
    ctx.beginPath();
    let started = false;
    for (let i = 0; i < Nvals.length; i++) {
      if (!isFinite(logE[i]) || logE[i] < -13) continue;
      if (!started) { ctx.moveTo(pxF(logN[i]), pyF(logE[i])); started = true; }
      else ctx.lineTo(pxF(logN[i]), pyF(logE[i]));
    }
    ctx.stroke();

    // Current N marker
    const N = parseInt(document.getElementById('nSlider').value);
    const curErr = Math.abs(riemannSum(N) - EXACT);
    if (curErr > 1e-14) {
      const cx = pxF(Math.log10(N)), cy = pyF(Math.log10(curErr));
      ctx.fillStyle = '#e67e22';
      ctx.beginPath(); ctx.arc(cx, cy, 6, 0, 2 * Math.PI); ctx.fill();
      ctx.fillStyle = '#e67e22'; ctx.font = 'bold 12px Arial';
      ctx.fillText(`N=${N}`, cx + 8, cy - 6);
    }

    ctx.fillStyle = '#2c3e50'; ctx.font = 'bold 13px Arial';
    ctx.fillText('Error convergence (log-log)', pad, pad - 18);
  }

  drawTrajectory();
  buildTable();
  update();
</script>
</body>
</html>
```

> **How to use the application:**
> - The top canvas shows the parabolic trajectory (blue) with the force field arrows (red) at five sample points along the path.
> - The slider controls $N$ — the number of subintervals in the Riemann sum.
> - The result box shows the numerical approximation, the exact value $5/3$, and the current error.
> - The convergence table lists errors for $N = 1, 2, 5, \ldots, 500$.
> - The log-log error plot shows slope $\approx -1$, confirming $O(1/N)$ convergence for the left-endpoint Riemann sum (first-order method).

---

## Summary

| Step | Result |
|---|---|
| Velocity vector | $\vec{v}(t) = (1,\ 2t)$ |
| Force along trajectory | $\vec{F}(t) = (t^2,\ 2t)$ |
| Dot product $\vec{F} \cdot \vec{v}$ | $t^2 \cdot 1 + 2t \cdot 2t = 5t^2$ |
| Work integral | $W = \int_0^1 5t^2\, dt$ |
| Analytical result | $W = 5/3 \approx 1.6\overline{6}$ |
| Riemann sum convergence | $O(1/N)$ — first order (left-endpoint rule) |

---

## 5 Possible Questions & Answers

---

**Q1: What is the physical meaning of the dot product $\vec{F} \cdot \vec{v}$ inside the integral?**

**A:** The dot product $\vec{F} \cdot \vec{v}$ gives the instantaneous **power** — the rate of work being done by the force at that moment (in units of energy per time). Only the component of force parallel to the velocity does work; the perpendicular component merely steers the object without adding energy. For example, at $t = 0.5$: $\vec{F} = (0.25, 1)$ and $\vec{v} = (1, 1)$, giving power $= 0.25 \cdot 1 + 1 \cdot 1 = 1.25$ — both components contribute positively, meaning the force is helping accelerate the object along the path. Integrating this power over time gives total work: energy transferred.

---

**Q2: Is the work done by this force path-independent? How would you check?**

**A:** A force is **conservative** (path-independent) if and only if its curl is zero: $\frac{\partial F_y}{\partial x} - \frac{\partial F_x}{\partial y} = 0$. For $\vec{F} = (y, 2x)$: $\frac{\partial (2x)}{\partial x} = 2$ and $\frac{\partial y}{\partial y} = 1$. Since $2 \neq 1$, the curl is $2 - 1 = 1 \neq 0$, so the force is **non-conservative**. This means the work done depends on which path is taken from start to finish — if you moved along a straight line from $(0,0)$ to $(1,1)$ instead of the parabola, you would get a different value of work. Non-conservative forces include friction, magnetic forces, and many physically realistic field configurations.

---

**Q3: How does the left-endpoint Riemann sum differ from the trapezoidal rule used in Problem 6, and why does it converge more slowly?**

**A:** The **left-endpoint Riemann sum** approximates the integrand as constant over each subinterval, using the value at the left endpoint. This is a first-order method with error $O(h) = O(1/N)$ — halving $h$ halves the error. The **trapezoidal rule** uses the average of the left and right endpoint values in each subinterval, making it second-order: error $O(h^2) = O(1/N^2)$. The trapezoidal rule is more accurate because it accounts for the slope of the integrand across each subinterval, not just its value at one end. On the log-log error plot, this is visible as a slope of $-1$ (Riemann) versus $-2$ (trapezoidal).

---

**Q4: What would the work be if the force were $\vec{F} = (-y, x)$ instead? Would it be positive or negative?**

**A:** For $\vec{F} = (-y, x)$, substituting $x = t$, $y = t^2$: $\vec{F}(t) = (-t^2, t)$. The dot product with $\vec{v} = (1, 2t)$: $(-t^2)(1) + (t)(2t) = -t^2 + 2t^2 = t^2$. The work would be $W = \int_0^1 t^2\,dt = 1/3 > 0$ — still positive. A useful check: the sign of work depends on whether the force and velocity are more aligned (positive) or opposed (negative) on average. For $\vec{F} = (-y, x)$ this is a rotation field (like a whirlpool), and the net work along this parabola happens to be positive because the $y$-component of the force ($x = t > 0$) aligns with the upward motion ($v_y = 2t > 0$) more than the $x$-component opposes it.

---

**Q5: How would the calculation change if the trajectory were a straight line from $(0,0)$ to $(1,1)$ instead of the parabola?**

**A:** A straight line from $(0,0)$ to $(1,1)$ can be parameterised as $x = t$, $y = t$, $t \in [0,1]$. Then $\vec{v} = (1, 1)$ and $\vec{F}(t) = (t, 2t)$. The dot product: $(t)(1) + (2t)(1) = 3t$. The work: $W = \int_0^1 3t\,dt = [3t^2/2]_0^1 = 3/2 = 1.5$. This differs from the parabolic result of $5/3 \approx 1.667$, confirming that the force is non-conservative — different paths give different amounts of work. The parabola does more work than the straight line because the object spends more time in regions where the force better aligns with the direction of motion.