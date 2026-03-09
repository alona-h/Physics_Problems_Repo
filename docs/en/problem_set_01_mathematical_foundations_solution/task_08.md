# Problem Set 1 – Problem 8: First-Order Differential Equation

---

## Overview

This problem introduces **ordinary differential equations (ODEs)** — equations that relate a function to its own derivative. Instead of asking "what is $y$ at a specific value of $t$?", a differential equation asks "what function $y(t)$ satisfies this relationship between $y$ and its rate of change?"

The equation here is:
$$\frac{dy}{dt} = -ky$$

> **Plain-language meaning:** The rate of change of $y$ is proportional to $y$ itself, but with a negative sign. If $y$ is large, it decreases quickly. If $y$ is small, it decreases slowly. This is the mathematical description of **exponential decay** — the same law that governs radioactive decay, cooling of objects, discharge of capacitors, and population decline.

---

## 8.1 – Solving the equation

### Method: Separation of Variables

The idea is to rearrange the equation so that all terms involving $y$ are on one side and all terms involving $t$ are on the other — then integrate both sides.

**Step 1 — Separate variables:**

Starting from:
$$\frac{dy}{dt} = -ky$$

Divide both sides by $y$ (assuming $y \neq 0$) and multiply both sides by $dt$:

$$\frac{dy}{y} = -k\, dt$$

> **Explanation:** We are treating $\frac{dy}{dt}$ as if it were a fraction and "separating" $dy$ from $dt$. This is a standard technique and is rigorously justified by the chain rule. The key requirement is that the equation can be written in the form $f(y)\,dy = g(t)\,dt$ — i.e. the $y$-parts and $t$-parts can be cleanly separated to opposite sides.

**Step 2 — Integrate both sides:**

$$\int \frac{dy}{y} = \int -k\, dt$$

$$\ln|y| = -kt + C$$

where $C$ is the constant of integration.

> **Explanation:** The left-hand integral $\int \frac{1}{y}\,dy = \ln|y|$ is a standard result. The right-hand integral $\int -k\,dt = -kt + C$ is straightforward since $k$ is a constant. The constant $C$ appears on one side only (we can absorb it there without loss of generality).

**Step 3 — Solve for $y$:**

Exponentiate both sides to undo the natural logarithm:

$$|y| = e^{-kt + C} = e^C \cdot e^{-kt}$$

Since $e^C$ is just a positive constant, we rename it $A = e^C > 0$. Dropping the absolute value (allowing $A$ to be any nonzero real number to cover both signs of $y$):

$$y(t) = A e^{-kt}$$

**Step 4 — Apply initial condition $y(0) = y_0$:**

$$y(0) = A e^{0} = A = y_0$$

Therefore $A = y_0$, and the **general solution** is:

$$\boxed{y(t) = y_0\, e^{-kt}}$$

> **Explanation:** The constant $A$ (equivalently $y_0$) is the value of $y$ at time $t = 0$ — the initial condition. Without it, we only know the *shape* of the solution (exponential decay), but not where it starts. The initial condition pins down the unique solution from the infinite family $y = Ae^{-kt}$. Every different starting value $y_0$ gives a different curve, all with the same exponential shape.

---

### Verification

Differentiate the solution and check it satisfies the original equation:

$$\frac{dy}{dt} = \frac{d}{dt}\left(y_0 e^{-kt}\right) = y_0 \cdot (-k) e^{-kt} = -k \underbrace{(y_0 e^{-kt})}_{= y} = -ky \checkmark$$

---

### Behaviour depending on $k$

| Value of $k$ | Behaviour of $y(t)$ | Physical example |
|---|---|---|
| $k > 0$ | Exponential **decay** toward 0 | Radioactive decay, cooling |
| $k = 0$ | Constant: $y(t) = y_0$ | No change |
| $k < 0$ | Exponential **growth** without bound | Population growth, compound interest |

> **Explanation:** The sign of $k$ completely determines the long-term fate of $y$. For $k > 0$, the negative feedback drives $y$ back toward zero — the larger $y$ is, the faster it falls. For $k < 0$, the equation becomes $dy/dt = |k|y$, a positive feedback loop where $y$ grows without limit. The parameter $1/k$ (for $k > 0$) is called the **time constant** $\tau$ — it is the time after which $y$ has decayed to $e^{-1} \approx 36.8\%$ of its initial value.

---

## 8.2 – HTML/JS Visualisation

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <title>Problem 8 – Exponential Decay/Growth</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 860px;
      margin: 40px auto;
      padding: 0 20px;
      background: #f8f9fa;
      color: #222;
    }
    h2 { color: #2c3e50; margin-bottom: 4px; }
    .subtitle { color: #666; margin-bottom: 20px; font-size: 0.95em; }
    .panel {
      background: white;
      border-radius: 8px;
      padding: 20px 24px;
      margin-bottom: 20px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.08);
    }
    canvas { display: block; margin: 0 auto; }
    .controls {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 14px 30px;
      margin-bottom: 16px;
    }
    .ctrl-row { display: flex; flex-direction: column; gap: 4px; }
    label { font-weight: bold; font-size: 0.93em; color: #2c3e50; }
    input[type=range] { width: 100%; }
    .val-display {
      font-size: 0.88em;
      color: #555;
      text-align: right;
    }
    .formula-box {
      background: #eaf4fb;
      border-left: 4px solid #2980b9;
      padding: 10px 16px;
      border-radius: 4px;
      font-size: 1.0em;
      margin-bottom: 14px;
    }
    .info-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;
      margin-top: 14px;
    }
    .info-card {
      background: #f0f4f8;
      border-radius: 6px;
      padding: 10px 14px;
      font-size: 0.88em;
      text-align: center;
    }
    .info-card b { display: block; font-size: 1.1em; color: #2c3e50; }
    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.89em;
      margin-top: 8px;
    }
    th, td { border: 1px solid #ddd; padding: 6px 10px; text-align: right; }
    th { background: #2c3e50; color: white; }
    tr:nth-child(even) { background: #f5f5f5; }
    h3 { margin: 0 0 14px 0; color: #2c3e50; }
  </style>
</head>
<body>

<h2>Problem 8 – First-Order ODE: dy/dt = −ky</h2>
<p class="subtitle">Solution: y(t) = y₀ · e<sup>−kt</sup></p>

<!-- CONTROLS -->
<div class="panel">
  <h3>Parameters</h3>
  <div class="controls">
    <div class="ctrl-row">
      <label>Decay constant k = <span id="kVal">1.00</span></label>
      <input type="range" id="kSlider" min="-2" max="3" step="0.05" value="1"
             oninput="document.getElementById('kVal').textContent=
               parseFloat(this.value).toFixed(2); draw()">
      <div class="val-display">Range: −2 to 3 &nbsp;(negative k → growth)</div>
    </div>
    <div class="ctrl-row">
      <label>Initial condition y(0) = <span id="y0Val">1.00</span></label>
      <input type="range" id="y0Slider" min="-3" max="3" step="0.1" value="1"
             oninput="document.getElementById('y0Val').textContent=
               parseFloat(this.value).toFixed(2); draw()">
      <div class="val-display">Range: −3 to 3</div>
    </div>
    <div class="ctrl-row">
      <label>Time range t ∈ [0, T],  T = <span id="tVal">5.0</span></label>
      <input type="range" id="tSlider" min="1" max="10" step="0.5" value="5"
             oninput="document.getElementById('tVal').textContent=
               parseFloat(this.value).toFixed(1); draw()">
      <div class="val-display">Range: 1 to 10</div>
    </div>
    <div class="ctrl-row">
      <label>Extra curves (different y₀)</label>
      <input type="range" id="curvesSlider" min="0" max="5" step="1" value="3"
             oninput="document.getElementById('curvesVal').textContent=
               this.value; draw()">
      <div class="val-display">
        Show <span id="curvesVal">3</span> additional initial conditions
      </div>
    </div>
  </div>

  <div class="formula-box" id="formulaBox"></div>

  <div class="info-grid" id="infoGrid"></div>
</div>

<!-- MAIN PLOT -->
<div class="panel">
  <h3>Solution curves y(t) = y₀ · e<sup>−kt</sup></h3>
  <canvas id="mainCanvas" width="780" height="380"></canvas>
</div>

<!-- PHASE PORTRAIT -->
<div class="panel">
  <h3>Phase portrait: dy/dt vs y &nbsp;(slope field)</h3>
  <canvas id="phaseCanvas" width="780" height="280"></canvas>
  <p style="color:#666; font-size:0.88em; text-align:center; margin-top:8px">
    Each arrow shows the direction of change at that point.
    Horizontal axis: y &nbsp;|&nbsp; Vertical axis: dy/dt = −ky
  </p>
</div>

<!-- TABLE -->
<div class="panel">
  <h3>Solution values at selected times</h3>
  <table id="valTable">
    <thead>
      <tr><th>t</th><th>y(t) = y₀·e^(−kt)</th>
          <th>dy/dt = −k·y(t)</th><th>% of y₀ remaining</th></tr>
    </thead>
    <tbody id="valBody"></tbody>
  </table>
</div>

<script>
  const COLORS = ['#2980b9','#e74c3c','#27ae60','#8e44ad','#e67e22','#16a085'];

  function getParams() {
    return {
      k:  parseFloat(document.getElementById('kSlider').value),
      y0: parseFloat(document.getElementById('y0Slider').value),
      T:  parseFloat(document.getElementById('tSlider').value),
      nExtra: parseInt(document.getElementById('curvesSlider').value)
    };
  }

  function y(t, k, y0) { return y0 * Math.exp(-k * t); }

  // ── Main solution plot ────────────────────────────────────────
  function drawMain(k, y0, T, nExtra) {
    const canvas = document.getElementById('mainCanvas');
    const ctx = canvas.getContext('2d');
    const W = canvas.width, H = canvas.height;
    const padL = 60, padR = 20, padT = 20, padB = 40;

    // Determine y-range from all curves
    const allY0s = [y0];
    for (let i = 1; i <= nExtra; i++) allY0s.push(y0 * (0.5 * i + 0.5));
    if (y0 > 0) allY0s.push(-y0 * 0.7);

    let yMin = Infinity, yMax = -Infinity;
    for (const y0c of allY0s) {
      const vals = [y0c, y(T, k, y0c)];
      yMin = Math.min(yMin, ...vals);
      yMax = Math.max(yMax, ...vals);
    }
    const pad = (yMax - yMin) * 0.1 || 0.5;
    yMin -= pad; yMax += pad;
    if (yMin > -0.1) yMin = -0.1;
    if (yMax < 0.1) yMax = 0.1;

    function px(t)  { return padL + (t / T) * (W - padL - padR); }
    function py(yv) { return padT + (1 - (yv - yMin) / (yMax - yMin)) * (H - padT - padB); }

    ctx.clearRect(0, 0, W, H);

    // Grid
    ctx.strokeStyle = '#efefef'; ctx.lineWidth = 1;
    for (let i = 0; i <= 5; i++) {
      const t = i * T / 5;
      ctx.beginPath(); ctx.moveTo(px(t), padT); ctx.lineTo(px(t), H - padB); ctx.stroke();
    }
    const nYGrid = 5;
    for (let i = 0; i <= nYGrid; i++) {
      const yv = yMin + i * (yMax - yMin) / nYGrid;
      ctx.beginPath(); ctx.moveTo(padL, py(yv)); ctx.lineTo(W - padR, py(yv)); ctx.stroke();
    }

    // Zero lines
    ctx.strokeStyle = '#aaa'; ctx.lineWidth = 1;
    if (yMin < 0 && yMax > 0) {
      ctx.beginPath(); ctx.moveTo(padL, py(0)); ctx.lineTo(W - padR, py(0)); ctx.stroke();
    }
    ctx.beginPath(); ctx.moveTo(padL, padT); ctx.lineTo(padL, H - padB);
    ctx.lineTo(W - padR, H - padB); ctx.stroke();

    // Axis labels
    ctx.fillStyle = '#555'; ctx.font = '12px Arial';
    for (let i = 0; i <= 5; i++) {
      const t = i * T / 5;
      ctx.fillText(t.toFixed(1), px(t) - 10, H - padB + 16);
    }
    for (let i = 0; i <= nYGrid; i++) {
      const yv = yMin + i * (yMax - yMin) / nYGrid;
      ctx.fillText(yv.toFixed(2), 2, py(yv) + 4);
    }
    ctx.fillStyle = '#2c3e50';
    ctx.fillText('t', W - padR + 4, H - padB + 4);
    ctx.save(); ctx.translate(14, H / 2); ctx.rotate(-Math.PI / 2);
    ctx.fillText('y(t)', -16, 0); ctx.restore();

    // Extra curves (different y0)
    const extraY0s = [];
    for (let i = 1; i <= nExtra; i++) extraY0s.push(y0 * (0.5 * i + 0.5));

    let ci = 1;
    for (const ey0 of extraY0s) {
      ctx.strokeStyle = COLORS[ci % COLORS.length];
      ctx.lineWidth = 1.5; ctx.setLineDash([5, 4]);
      ctx.beginPath();
      for (let n = 0; n <= 400; n++) {
        const t = n / 400 * T;
        n === 0 ? ctx.moveTo(px(t), py(y(t, k, ey0)))
                : ctx.lineTo(px(t), py(y(t, k, ey0)));
      }
      ctx.stroke(); ctx.setLineDash([]);
      ctx.fillStyle = COLORS[ci % COLORS.length];
      ctx.font = '11px Arial';
      ctx.fillText(`y₀=${ey0.toFixed(1)}`, px(0) + 4, py(ey0) - 5);
      ci++;
    }

    // Main curve
    ctx.strokeStyle = COLORS[0]; ctx.lineWidth = 2.5;
    ctx.beginPath();
    for (let n = 0; n <= 400; n++) {
      const t = n / 400 * T;
      n === 0 ? ctx.moveTo(px(t), py(y(t, k, y0)))
              : ctx.lineTo(px(t), py(y(t, k, y0)));
    }
    ctx.stroke();

    // Tangent line at t=0
    const slope0 = -k * y0;
    const t1tang = Math.min(T * 0.2, 1.5);
    ctx.strokeStyle = '#e74c3c'; ctx.lineWidth = 1.5; ctx.setLineDash([4, 3]);
    ctx.beginPath();
    ctx.moveTo(px(0), py(y0));
    ctx.lineTo(px(t1tang), py(y0 + slope0 * t1tang));
    ctx.stroke(); ctx.setLineDash([]);
    ctx.fillStyle = '#e74c3c'; ctx.font = '11px Arial';
    ctx.fillText('tangent at t=0', px(t1tang * 0.3), py(y0 + slope0 * t1tang * 0.3) - 8);

    // Half-life / doubling time marker
    if (k !== 0) {
      const tHalf = Math.log(2) / Math.abs(k);
      if (tHalf < T) {
        const yHalf = y(tHalf, k, y0);
        ctx.fillStyle = '#27ae60';
        ctx.beginPath(); ctx.arc(px(tHalf), py(yHalf), 5, 0, 2 * Math.PI); ctx.fill();
        ctx.font = 'bold 11px Arial';
        ctx.fillText(k > 0 ? `t½ = ${tHalf.toFixed(2)}` : `t×2 = ${tHalf.toFixed(2)}`,
          px(tHalf) + 7, py(yHalf) - 6);
        // dashed drop line
        ctx.strokeStyle = '#27ae60'; ctx.lineWidth = 1; ctx.setLineDash([3, 3]);
        ctx.beginPath();
        ctx.moveTo(px(tHalf), py(yHalf));
        ctx.lineTo(px(tHalf), H - padB);
        ctx.stroke(); ctx.setLineDash([]);
      }
    }

    // Start dot
    ctx.fillStyle = COLORS[0];
    ctx.beginPath(); ctx.arc(px(0), py(y0), 5, 0, 2 * Math.PI); ctx.fill();
    ctx.fillStyle = '#2c3e50'; ctx.font = 'bold 12px Arial';
    ctx.fillText(`y(0) = ${y0.toFixed(2)}`, px(0) + 8, py(y0) - 8);
  }

  // ── Phase portrait ────────────────────────────────────────────
  function drawPhase(k, y0, T) {
    const canvas = document.getElementById('phaseCanvas');
    const ctx = canvas.getContext('2d');
    const W = canvas.width, H = canvas.height;
    const padL = 60, padR = 20, padT = 20, padB = 35;

    const yRange = Math.max(Math.abs(y0) * 1.5, 2);
    const yMin = -yRange, yMax = yRange;
    const dydtMin = -k * yMax - 0.2, dydtMax = -k * yMin + 0.2;

    function px(yv) {
      return padL + (yv - yMin) / (yMax - yMin) * (W - padL - padR);
    }
    function py(dydt) {
      return padT + (1 - (dydt - dydtMin) / (dydtMax - dydtMin)) * (H - padT - padB);
    }

    ctx.clearRect(0, 0, W, H);

    // Grid
    ctx.strokeStyle = '#efefef'; ctx.lineWidth = 1;
    for (let i = -4; i <= 4; i++) {
      const yv = i * yRange / 4;
      ctx.beginPath(); ctx.moveTo(px(yv), padT); ctx.lineTo(px(yv), H - padB); ctx.stroke();
    }

    // Axes
    ctx.strokeStyle = '#aaa'; ctx.lineWidth = 1.5;
    ctx.beginPath();
    ctx.moveTo(padL, padT); ctx.lineTo(padL, H - padB);
    ctx.lineTo(W - padR, H - padB); ctx.stroke();
    // zero-dydt line
    if (dydtMin < 0 && dydtMax > 0) {
      ctx.beginPath();
      ctx.moveTo(padL, py(0)); ctx.lineTo(W - padR, py(0)); ctx.stroke();
    }

    // dy/dt = -ky  →  straight line through origin
    ctx.strokeStyle = '#2980b9'; ctx.lineWidth = 2.5;
    ctx.beginPath();
    ctx.moveTo(px(yMin), py(-k * yMin));
    ctx.lineTo(px(yMax), py(-k * yMax));
    ctx.stroke();

    // Slope arrows
    const nArrows = 12;
    for (let i = 0; i <= nArrows; i++) {
      const yv = yMin + i * (yMax - yMin) / nArrows;
      const dydt = -k * yv;
      const sc = 0.18 * (yMax - yMin) / nArrows;
      const len = Math.sqrt(1 + dydt * dydt / ((yMax - yMin) * (yMax - yMin)));
      const dx = sc / len, dDydt = (dydt / (yMax - yMin)) * sc / len;
      const x0 = px(yv), y0p = py(dydt);
      drawArrow2(ctx, x0 - dx * 40, y0p + dDydt * 40,
                      x0 + dx * 40, y0p - dDydt * 40, '#e74c3c', 1.5);
    }

    // Axis labels
    ctx.fillStyle = '#555'; ctx.font = '12px Arial';
    for (let i = -4; i <= 4; i++) {
      const yv = i * yRange / 4;
      ctx.fillText(yv.toFixed(1), px(yv) - 12, H - padB + 16);
    }
    ctx.fillStyle = '#2c3e50';
    ctx.fillText('y', W - padR + 4, H - padB + 4);
    ctx.save(); ctx.translate(14, H / 2); ctx.rotate(-Math.PI / 2);
    ctx.fillText('dy/dt', -20, 0); ctx.restore();

    ctx.fillStyle = '#2980b9'; ctx.font = 'bold 12px Arial';
    ctx.fillText(`dy/dt = −${k.toFixed(2)} · y   (slope = −k = ${(-k).toFixed(2)})`,
      padL + 10, padT + 18);
  }

  function drawArrow2(ctx, x1, y1, x2, y2, color, lw) {
    const dx = x2 - x1, dy = y2 - y1;
    const angle = Math.atan2(dy, dx);
    const hs = 7;
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

  // ── Update formula box and info cards ────────────────────────
  function updateFormula(k, y0, T) {
    const sign = k >= 0 ? '' : '+';
    document.getElementById('formulaBox').innerHTML =
      `<b>Solution:</b> &nbsp; y(t) = ${y0.toFixed(2)} · e<sup>${sign}${(-k).toFixed(2)}t</sup>` +
      `&nbsp;&nbsp;&nbsp; (k = ${k.toFixed(2)}, &nbsp; y₀ = ${y0.toFixed(2)})`;

    const tHalf = k !== 0 ? (Math.log(2) / Math.abs(k)).toFixed(3) : '∞';
    const tau   = k !== 0 ? (1 / Math.abs(k)).toFixed(3) : '∞';
    const yAtT  = y(T, k, y0).toFixed(4);
    const label = k > 0 ? 'Half-life t½' : k < 0 ? 'Doubling time' : 'Half-life t½';
    document.getElementById('infoGrid').innerHTML =
      `<div class="info-card"><b>${tHalf}</b>${label}</div>` +
      `<div class="info-card"><b>${tau}</b>Time constant τ = 1/|k|</div>` +
      `<div class="info-card"><b>${yAtT}</b>y at t = T = ${T.toFixed(1)}</div>`;
  }

  // ── Solution value table ──────────────────────────────────────
  function buildTable(k, y0, T) {
    const times = [0, 0.25, 0.5, 1, 1.5, 2, 3, 5, T].filter(t => t <= T);
    const unique = [...new Set(times)].sort((a, b) => a - b);
    const tbody = document.getElementById('valBody');
    tbody.innerHTML = '';
    for (const t of unique) {
      const yv  = y(t, k, y0);
      const dydtv = -k * yv;
      const pct = y0 !== 0 ? (yv / y0 * 100).toFixed(2) : '—';
      const tr = document.createElement('tr');
      tr.innerHTML =
        `<td>${t.toFixed(2)}</td>` +
        `<td>${yv.toFixed(6)}</td>` +
        `<td>${dydtv.toFixed(6)}</td>` +
        `<td>${pct}%</td>`;
      tbody.appendChild(tr);
    }
  }

  // ── Master draw ───────────────────────────────────────────────
  function draw() {
    const { k, y0, T, nExtra } = getParams();
    updateFormula(k, y0, T);
    drawMain(k, y0, T, nExtra);
    drawPhase(k, y0, T);
    buildTable(k, y0, T);
  }

  draw();
</script>
</body>
</html>
```

> **How to use the application:**
> - **k slider** — drag right for faster decay, left past zero for exponential growth.
> - **y₀ slider** — sets the starting value; try negative values to see the curve below the axis.
> - **T slider** — extends or compresses the time window.
> - **Extra curves slider** — adds dashed curves for different initial conditions with the same $k$, showing the full *family* of solutions.
> - The **info cards** show the half-life $t_{1/2} = \ln 2 / k$, the time constant $\tau = 1/k$, and the value of $y$ at the end of the time window.
> - The **phase portrait** shows $dy/dt$ as a function of $y$ — a straight line through the origin with slope $-k$. The red arrows indicate the direction of change at each value of $y$.
> - The **solution table** gives numerical values at selected time points.

---

## Summary

| Quantity | Expression |
|---|---|
| ODE | $dy/dt = -ky$ |
| Method | Separation of variables |
| General solution | $y(t) = A e^{-kt}$ |
| With initial condition | $y(t) = y_0\,e^{-kt}$ |
| Half-life ($k > 0$) | $t_{1/2} = \ln 2\, /\, k \approx 0.693/k$ |
| Time constant | $\tau = 1/k$ (time to decay to $e^{-1} \approx 36.8\%$) |
| Behaviour for $k > 0$ | Exponential decay to 0 |
| Behaviour for $k < 0$ | Exponential growth to $\pm\infty$ |
| Behaviour for $k = 0$ | Constant $y(t) = y_0$ |

---

## 5 Possible Questions & Answers

---

**Q1: Why is separation of variables valid? Are there restrictions on when it can be used?**

**A:** Separation of variables works when the ODE can be written as $f(y)\,dy = g(t)\,dt$ — i.e. the right-hand side factors into a product of a function of $y$ only and a function of $t$ only. For $dy/dt = -ky$, this factoring is immediate: $\frac{dy}{y} = -k\,dt$. The technique is valid as long as $y \neq 0$ (we divided by $y$). The case $y = 0$ is actually a separate solution — the trivial solution $y(t) = 0$ for all $t$ — which satisfies the ODE trivially since both sides equal zero. For initial conditions $y_0 \neq 0$, the exponential solution is the correct one and never crosses zero in finite time (since $e^{-kt} \neq 0$ for any finite $t$).

---

**Q2: What is the half-life $t_{1/2}$ and how is it derived from the solution?**

**A:** The half-life $t_{1/2}$ is the time at which $y$ has decreased to half its initial value: $y(t_{1/2}) = y_0/2$. Setting up the equation:
$$y_0 e^{-k t_{1/2}} = \frac{y_0}{2}$$
Dividing both sides by $y_0$ and taking the natural log:
$$-k t_{1/2} = \ln\!\left(\frac{1}{2}\right) = -\ln 2$$
$$t_{1/2} = \frac{\ln 2}{k} \approx \frac{0.693}{k}$$
The half-life depends only on $k$, not on the initial value $y_0$. This is the hallmark of exponential decay: it takes the same time to go from $100$ to $50$ as from $50$ to $25$, or from $10$ to $5$.

---

**Q3: What is the time constant $\tau$ and how does it differ from the half-life?**

**A:** The time constant $\tau = 1/k$ is the time at which $y$ has decayed to $e^{-1} \approx 36.8\%$ of its initial value:
$$y(\tau) = y_0 e^{-k \cdot (1/k)} = y_0 e^{-1} \approx 0.368\, y_0$$
The half-life and time constant are related by $t_{1/2} = \tau \ln 2 \approx 0.693\,\tau$. The time constant is more natural in physics and engineering (e.g. RC circuits), while the half-life is more common in nuclear physics and medicine. Both characterise the same decay rate — they are just different reference thresholds (50% vs $\approx$37%).

---

**Q4: How would you solve $dy/dt = -ky + c$ where $c$ is a constant (non-homogeneous case)?**

**A:** This is a **non-homogeneous** linear ODE. The standard approach is: (1) find the equilibrium by setting $dy/dt = 0$: $y^* = c/k$. (2) Substitute $u = y - y^*$ to shift the equation: $du/dt = d(y - y^*)/dt = dy/dt = -k(u + y^*) + c = -ku$. This is the same homogeneous equation in $u$, so $u(t) = (y_0 - y^*) e^{-kt}$. (3) Translate back: $y(t) = y^* + (y_0 - y^*)e^{-kt} = \frac{c}{k} + \left(y_0 - \frac{c}{k}\right)e^{-kt}$. The solution still decays exponentially, but now toward the non-zero equilibrium $c/k$ rather than toward zero.

---

**Q5: Give three real-world phenomena modelled by $dy/dt = -ky$ and identify what $y$, $k$, and $t$ represent in each.**

**A:**
- **Radioactive decay:** $y$ = number of radioactive atoms, $k$ = decay constant (related to the isotope's half-life), $t$ = time. The equation says each atom decays independently with constant probability per unit time, giving exponential decrease in the total count.
- **Newton's law of cooling:** $y$ = temperature difference between an object and its surroundings, $k$ = heat transfer coefficient (depends on material and surface area), $t$ = time. The object cools faster when the temperature gap is large, slower as it approaches room temperature — classic exponential decay of the temperature difference.
- **Capacitor discharge:** $y$ = charge $Q$ on a capacitor discharging through a resistor $R$ with capacitance $C$, $k = 1/(RC)$, $t$ = time. The voltage (and charge) decays exponentially with time constant $\tau = RC$. This is why electronics engineers talk about "RC time constants" when designing timing circuits.