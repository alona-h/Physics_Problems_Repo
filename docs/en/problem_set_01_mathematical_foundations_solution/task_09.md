# Problem Set 1 – Problem 9: Harmonic Oscillator

---

## Overview

The **harmonic oscillator** is one of the most important equations in all of physics and engineering. It describes any system where a restoring force pulls an object back toward an equilibrium position with a strength proportional to the displacement. Examples include:

- A mass on a spring (Hooke's law)
- A pendulum for small angles
- An LC electrical circuit
- Vibrations of atoms in a crystal
- Sound waves, light waves

The equation is:
$$\frac{d^2x}{dt^2} + \omega^2 x = 0$$

> **Plain-language meaning:** The second derivative of $x$ (acceleration) is proportional to $x$ itself, but with a negative sign. If the object is displaced to the right ($x > 0$), the acceleration points left ($\ddot{x} < 0$) — restoring it. If displaced left ($x < 0$), the acceleration points right. This creates perpetual oscillation.

The constant $\omega$ (omega) is the **angular frequency** of oscillation, measured in radians per second. It is related to the ordinary frequency $f$ and period $T$ by:
$$\omega = 2\pi f = \frac{2\pi}{T}$$

---

## 9.1 – General solution

### Method: Characteristic equation

For a **second-order linear ODE with constant coefficients**, we try a solution of the form $x(t) = e^{\lambda t}$ and find which values of $\lambda$ work.

**Step 1 — Substitute $x = e^{\lambda t}$ into the ODE:**

$$\frac{d^2}{dt^2}(e^{\lambda t}) + \omega^2 e^{\lambda t} = 0$$

$$\lambda^2 e^{\lambda t} + \omega^2 e^{\lambda t} = 0$$

Factor out $e^{\lambda t}$ (which is never zero):

$$e^{\lambda t}(\lambda^2 + \omega^2) = 0 \implies \lambda^2 + \omega^2 = 0$$

**Step 2 — Solve the characteristic equation:**

$$\lambda^2 = -\omega^2$$

$$\lambda = \pm\sqrt{-\omega^2} = \pm i\omega$$

where $i = \sqrt{-1}$ is the imaginary unit. We get two **complex conjugate roots**: $\lambda_1 = +i\omega$ and $\lambda_2 = -i\omega$.

> **Explanation:** The appearance of imaginary numbers here is not a problem — it is the mathematical signal that the solution will be oscillatory rather than exponential. Complex roots always come in conjugate pairs for real-valued ODEs, and the resulting real solution is built from sines and cosines via Euler's formula: $e^{i\theta} = \cos\theta + i\sin\theta$.

**Step 3 — Write the general solution:**

For complex roots $\lambda = \pm i\omega$, the general **real-valued** solution is:

$$\boxed{x(t) = C_1 \cos(\omega t) + C_2 \sin(\omega t)}$$

where $C_1$ and $C_2$ are arbitrary real constants determined by initial conditions.

> **Why cosine and sine?** Starting from the complex exponentials $e^{i\omega t}$ and $e^{-i\omega t}$, Euler's formula gives:
> $$e^{i\omega t} = \cos(\omega t) + i\sin(\omega t)$$
> $$e^{-i\omega t} = \cos(\omega t) - i\sin(\omega t)$$
> Taking real combinations: $\frac{e^{i\omega t} + e^{-i\omega t}}{2} = \cos(\omega t)$ and $\frac{e^{i\omega t} - e^{-i\omega t}}{2i} = \sin(\omega t)$. These are both real-valued solutions, and every real solution is a linear combination of them.

**Alternative form — amplitude and phase:**

The general solution can equivalently be written as:

$$x(t) = A\cos(\omega t + \phi)$$

where:
- $A = \sqrt{C_1^2 + C_2^2}$ is the **amplitude** (maximum displacement)
- $\phi = \arctan(-C_2/C_1)$ is the **phase angle** (shifts the cosine left or right in time)

This form makes the physical oscillation more transparent.

---

## 9.2 – Solving for given initial conditions

**Given initial conditions:**
$$x(0) = x_0, \qquad x'(0) = v_0$$

(where $x_0$ is the initial displacement and $v_0$ is the initial velocity)

**Step 1 — Apply $x(0) = x_0$:**

$$x(0) = C_1\cos(0) + C_2\sin(0) = C_1 \cdot 1 + C_2 \cdot 0 = C_1$$

$$\therefore \quad C_1 = x_0$$

**Step 2 — Differentiate $x(t)$ to get $x'(t)$:**

$$x'(t) = -C_1\omega\sin(\omega t) + C_2\omega\cos(\omega t)$$

**Step 3 — Apply $x'(0) = v_0$:**

$$x'(0) = -C_1\omega\sin(0) + C_2\omega\cos(0) = 0 + C_2\omega = C_2\omega$$

$$\therefore \quad C_2 = \frac{v_0}{\omega}$$

**Step 4 — Write the particular solution:**

$$\boxed{x(t) = x_0\cos(\omega t) + \frac{v_0}{\omega}\sin(\omega t)}$$

**Step 5 — Compute $x'(t)$ and $x''(t)$:**

$$x'(t) = -x_0\omega\sin(\omega t) + v_0\cos(\omega t)$$

$$x''(t) = -x_0\omega^2\cos(\omega t) - v_0\omega\sin(\omega t) = -\omega^2\underbrace{\left(x_0\cos(\omega t) + \frac{v_0}{\omega}\sin(\omega t)\right)}_{= x(t)}$$

$$\boxed{x''(t) = -\omega^2 x(t)}$$

**Verification:** $x'' + \omega^2 x = -\omega^2 x + \omega^2 x = 0$ ✓

> **Explanation:** The two initial conditions $x(0) = x_0$ and $x'(0) = v_0$ uniquely determine the two constants $C_1$ and $C_2$. This is expected: a second-order ODE needs exactly two pieces of initial information to pin down a unique solution from the two-parameter family. Physically, knowing where the oscillator starts *and* how fast it is moving at that moment completely determines its future motion forever.

**Amplitude of the particular solution:**

$$A = \sqrt{C_1^2 + C_2^2} = \sqrt{x_0^2 + \frac{v_0^2}{\omega^2}}$$

**Special cases:**

| Initial condition | Result |
|---|---|
| $x_0 = A,\ v_0 = 0$ | $x(t) = A\cos(\omega t)$ — starts at max displacement, zero velocity |
| $x_0 = 0,\ v_0 = v$ | $x(t) = \frac{v}{\omega}\sin(\omega t)$ — starts at equilibrium, maximum velocity |
| $x_0 = A,\ v_0 = A\omega$ | Full general case with both amplitude and phase shift |

---

## 9.3 – HTML/JS Visualisation

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <title>Problem 9 – Harmonic Oscillator</title>
  <style>
    * { box-sizing: border-box; }
    body {
      font-family: Arial, sans-serif;
      max-width: 900px;
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
    h3 { margin: 0 0 14px; color: #2c3e50; }
    canvas { display: block; margin: 0 auto; }
    .controls {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 12px 24px;
      margin-bottom: 16px;
    }
    .ctrl-row { display: flex; flex-direction: column; gap: 4px; }
    label { font-weight: bold; font-size: 0.91em; color: #2c3e50; }
    input[type=range] { width: 100%; }
    .val-display { font-size: 0.82em; color: #777; }
    .formula-box {
      background: #eaf4fb;
      border-left: 4px solid #2980b9;
      padding: 10px 16px;
      border-radius: 4px;
      font-size: 0.97em;
      margin-bottom: 14px;
      line-height: 1.7;
    }
    .info-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
      margin-top: 12px;
    }
    .info-card {
      background: #f0f4f8;
      border-radius: 6px;
      padding: 9px 12px;
      font-size: 0.86em;
      text-align: center;
    }
    .info-card b { display: block; font-size: 1.1em; color: #2c3e50; margin-bottom: 2px; }
    .legend {
      display: flex;
      gap: 20px;
      justify-content: center;
      margin-top: 8px;
      font-size: 0.88em;
    }
    .leg-item { display: flex; align-items: center; gap: 6px; }
    .leg-swatch { width: 28px; height: 3px; display: inline-block; border-radius: 2px; }
    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.88em;
      margin-top: 8px;
    }
    th, td { border: 1px solid #ddd; padding: 5px 10px; text-align: right; }
    th { background: #2c3e50; color: white; }
    tr:nth-child(even) { background: #f5f5f5; }
  </style>
</head>
<body>

<h2>Problem 9 – Harmonic Oscillator: x'' + ω²x = 0</h2>
<p class="subtitle">General solution: x(t) = x₀cos(ωt) + (v₀/ω)sin(ωt)</p>

<!-- CONTROLS -->
<div class="panel">
  <h3>Parameters & Initial Conditions</h3>
  <div class="controls">
    <div class="ctrl-row">
      <label>Angular frequency ω = <span id="wVal">1.00</span> rad/s</label>
      <input type="range" id="wSlider" min="0.2" max="4" step="0.1" value="1"
             oninput="document.getElementById('wVal').textContent=
               parseFloat(this.value).toFixed(2); draw()">
      <div class="val-display">Period T = 2π/ω</div>
    </div>
    <div class="ctrl-row">
      <label>Initial position x(0) = x₀ = <span id="x0Val">1.00</span></label>
      <input type="range" id="x0Slider" min="-3" max="3" step="0.1" value="1"
             oninput="document.getElementById('x0Val').textContent=
               parseFloat(this.value).toFixed(2); draw()">
      <div class="val-display">Displacement at t = 0</div>
    </div>
    <div class="ctrl-row">
      <label>Initial velocity x'(0) = v₀ = <span id="v0Val">0.00</span></label>
      <input type="range" id="v0Slider" min="-4" max="4" step="0.1" value="0"
             oninput="document.getElementById('v0Val').textContent=
               parseFloat(this.value).toFixed(2); draw()">
      <div class="val-display">Velocity at t = 0</div>
    </div>
    <div class="ctrl-row">
      <label>Time window T_max = <span id="tmaxVal">4</span> periods</label>
      <input type="range" id="tmaxSlider" min="1" max="10" step="1" value="4"
             oninput="document.getElementById('tmaxVal').textContent=
               this.value; draw()">
      <div class="val-display">Number of periods to display</div>
    </div>
    <div class="ctrl-row">
      <label>Show derivatives</label>
      <input type="range" id="derivSlider" min="0" max="2" step="1" value="1"
             oninput="document.getElementById('derivVal').textContent=
               ['x(t) only','x(t) and x\'(t)','all three'][this.value]; draw()">
      <div class="val-display"><span id="derivVal">x(t) and x'(t)</span></div>
    </div>
    <div class="ctrl-row">
      <label>Phase portrait</label>
      <input type="range" id="phaseSlider" min="0" max="1" step="1" value="1"
             oninput="document.getElementById('phaseLabel').textContent=
               this.value=='1'?'Shown':'Hidden'; draw()">
      <div class="val-display"><span id="phaseLabel">Shown</span></div>
    </div>
  </div>
  <div class="formula-box" id="formulaBox"></div>
  <div class="info-grid" id="infoGrid"></div>
</div>

<!-- MAIN TIME PLOT -->
<div class="panel">
  <h3>x(t), x'(t), x''(t) vs time</h3>
  <canvas id="mainCanvas" width="840" height="340"></canvas>
  <div class="legend" id="legend"></div>
</div>

<!-- PHASE PORTRAIT -->
<div class="panel" id="phasePanel">
  <h3>Phase portrait: x'(t) vs x(t)</h3>
  <canvas id="phaseCanvas" width="840" height="320"></canvas>
  <p style="color:#666;font-size:0.87em;text-align:center;margin-top:6px">
    An ellipse in phase space — the hallmark of undamped oscillation.
    The trajectory loops forever in the same closed path.
  </p>
</div>

<!-- TABLE -->
<div class="panel">
  <h3>Solution values at selected times</h3>
  <table>
    <thead>
      <tr>
        <th>t</th>
        <th>x(t)</th>
        <th>x'(t)</th>
        <th>x''(t)</th>
        <th>Energy ½(x'²+ω²x²)</th>
      </tr>
    </thead>
    <tbody id="valBody"></tbody>
  </table>
</div>

<script>
  const COL = { x: '#2980b9', xp: '#e74c3c', xpp: '#27ae60', phase: '#8e44ad' };

  function getP() {
    return {
      w:    parseFloat(document.getElementById('wSlider').value),
      x0:   parseFloat(document.getElementById('x0Slider').value),
      v0:   parseFloat(document.getElementById('v0Slider').value),
      nPer: parseInt(document.getElementById('tmaxSlider').value),
      deriv: parseInt(document.getElementById('derivSlider').value),
      showPhase: document.getElementById('phaseSlider').value === '1'
    };
  }

  function xFn(t, w, x0, v0)   { return x0*Math.cos(w*t) + (v0/w)*Math.sin(w*t); }
  function xpFn(t, w, x0, v0)  { return -x0*w*Math.sin(w*t) + v0*Math.cos(w*t); }
  function xppFn(t, w, x0, v0) { return -w*w*(x0*Math.cos(w*t) + (v0/w)*Math.sin(w*t)); }

  // ── Axes helper ───────────────────────────────────────────────
  function makeAxes(ctx, W, H, padL, padR, padT, padB,
                    tMax, yMin, yMax, nTick=5) {
    // grid
    ctx.strokeStyle = '#efefef'; ctx.lineWidth = 1;
    for (let i=0; i<=nTick; i++) {
      const t = i*tMax/nTick;
      const xp = padL + (t/tMax)*(W-padL-padR);
      ctx.beginPath(); ctx.moveTo(xp,padT); ctx.lineTo(xp,H-padB); ctx.stroke();
      const yv = yMin + i*(yMax-yMin)/nTick;
      const yp = padT + (1-(yv-yMin)/(yMax-yMin))*(H-padT-padB);
      ctx.beginPath(); ctx.moveTo(padL,yp); ctx.lineTo(W-padR,yp); ctx.stroke();
    }
    // zero line
    if (yMin < 0 && yMax > 0) {
      const y0p = padT + (1-(0-yMin)/(yMax-yMin))*(H-padT-padB);
      ctx.strokeStyle='#bbb'; ctx.lineWidth=1;
      ctx.beginPath(); ctx.moveTo(padL,y0p); ctx.lineTo(W-padR,y0p); ctx.stroke();
    }
    // axes
    ctx.strokeStyle='#999'; ctx.lineWidth=1.5;
    ctx.beginPath();
    ctx.moveTo(padL,padT); ctx.lineTo(padL,H-padB);
    ctx.lineTo(W-padR,H-padB); ctx.stroke();
    // labels
    ctx.fillStyle='#555'; ctx.font='11px Arial';
    for (let i=0; i<=nTick; i++) {
      const t = i*tMax/nTick;
      const xp = padL+(t/tMax)*(W-padL-padR);
      ctx.fillText(t.toFixed(1), xp-10, H-padB+15);
      const yv = yMin+i*(yMax-yMin)/nTick;
      const yp = padT+(1-(yv-yMin)/(yMax-yMin))*(H-padT-padB);
      ctx.fillText(yv.toFixed(2), 2, yp+4);
    }
  }

  function plotCurve(ctx, fn, W, H, padL, padR, padT, padB,
                     tMax, yMin, yMax, color, lw, dash=[]) {
    ctx.strokeStyle=color; ctx.lineWidth=lw; ctx.setLineDash(dash);
    ctx.beginPath();
    for (let i=0; i<=600; i++) {
      const t = i/600*tMax;
      const xp = padL+(t/tMax)*(W-padL-padR);
      const yp = padT+(1-(fn(t)-yMin)/(yMax-yMin))*(H-padT-padB);
      i===0 ? ctx.moveTo(xp,yp) : ctx.lineTo(xp,yp);
    }
    ctx.stroke(); ctx.setLineDash([]);
  }

  // ── Main time plot ────────────────────────────────────────────
  function drawMain(w, x0, v0, nPer, deriv) {
    const canvas = document.getElementById('mainCanvas');
    const ctx = canvas.getContext('2d');
    const W=canvas.width, H=canvas.height;
    const padL=55, padR=15, padT=20, padB=35;
    ctx.clearRect(0,0,W,H);

    const T  = 2*Math.PI/w;
    const tMax = nPer*T;
    const A  = Math.sqrt(x0*x0 + v0*v0/(w*w));
    const Ap = w*A;
    const App = w*w*A;
    const yMax = Math.max(A, deriv>=1?Ap:0, deriv>=2?App:0)*1.15 || 1;
    const yMin = -yMax;

    makeAxes(ctx,W,H,padL,padR,padT,padB,tMax,yMin,yMax);

    if (deriv>=2) plotCurve(ctx, t=>xppFn(t,w,x0,v0),
      W,H,padL,padR,padT,padB,tMax,yMin,yMax,COL.xpp,1.5,[5,4]);
    if (deriv>=1) plotCurve(ctx, t=>xpFn(t,w,x0,v0),
      W,H,padL,padR,padT,padB,tMax,yMin,yMax,COL.xp,1.8,[6,3]);
    plotCurve(ctx, t=>xFn(t,w,x0,v0),
      W,H,padL,padR,padT,padB,tMax,yMin,yMax,COL.x,2.5);

    // Period marker
    const px1 = padL, px2 = padL+(T/tMax)*(W-padL-padR);
    const my = padT+10;
    ctx.strokeStyle='#e67e22'; ctx.lineWidth=1.2;
    ctx.beginPath(); ctx.moveTo(px1,my); ctx.lineTo(px2,my); ctx.stroke();
    ctx.fillStyle='#e67e22'; ctx.font='bold 11px Arial';
    ctx.fillText(`T = ${T.toFixed(2)}s`, (px1+px2)/2-20, my-4);
    // tick marks
    ctx.beginPath(); ctx.moveTo(px1,my-4); ctx.lineTo(px1,my+4); ctx.stroke();
    ctx.beginPath(); ctx.moveTo(px2,my-4); ctx.lineTo(px2,my+4); ctx.stroke();

    // Amplitude marker
    const axp = padL + (0.25*T/tMax)*(W-padL-padR);
    const ayp = padT+(1-(A-yMin)/(yMax-yMin))*(H-padT-padB);
    ctx.fillStyle=COL.x; ctx.beginPath(); ctx.arc(axp,ayp,4,0,2*Math.PI); ctx.fill();
    ctx.font='bold 11px Arial';
    ctx.fillText(`A=${A.toFixed(3)}`, axp+6, ayp-4);

    // Axis labels
    ctx.fillStyle='#2c3e50'; ctx.font='12px Arial';
    ctx.fillText('t (s)', W-padR+2, H-padB+4);
    ctx.save(); ctx.translate(13,H/2); ctx.rotate(-Math.PI/2);
    ctx.fillText('displacement / velocity / accel.', -80, 0); ctx.restore();
  }

  // ── Phase portrait ────────────────────────────────────────────
  function drawPhase(w, x0, v0) {
    const canvas = document.getElementById('phaseCanvas');
    const ctx = canvas.getContext('2d');
    const W=canvas.width, H=canvas.height;
    const padL=60, padR=20, padT=25, padB=40;
    ctx.clearRect(0,0,W,H);

    const A  = Math.sqrt(x0*x0+v0*v0/(w*w));
    const Ap = w*A;
    const rng = Math.max(A,Ap)*1.25 || 1;
    const xMin=-rng, xMax=rng, yMin=-rng*1.1, yMax=rng*1.1;

    function px(xv){ return padL+(xv-xMin)/(xMax-xMin)*(W-padL-padR); }
    function py(yv){ return padT+(1-(yv-yMin)/(yMax-yMin))*(H-padT-padB); }

    // grid
    ctx.strokeStyle='#efefef'; ctx.lineWidth=1;
    for (let v=-2;v<=2;v++) {
      const xv=v*rng/2;
      ctx.beginPath(); ctx.moveTo(px(xv),padT); ctx.lineTo(px(xv),H-padB); ctx.stroke();
      ctx.beginPath(); ctx.moveTo(padL,py(xv)); ctx.lineTo(W-padR,py(xv)); ctx.stroke();
    }
    // axes
    ctx.strokeStyle='#aaa'; ctx.lineWidth=1.5;
    ctx.beginPath(); ctx.moveTo(px(0),padT); ctx.lineTo(px(0),H-padB); ctx.stroke();
    ctx.beginPath(); ctx.moveTo(padL,py(0)); ctx.lineTo(W-padR,py(0)); ctx.stroke();

    // Ellipse: x = A cos(wt+phi), x' = -Aw sin(wt+phi)
    // => (x/A)² + (x'/(Aw))² = 1
    ctx.strokeStyle=COL.phase; ctx.lineWidth=2.5;
    ctx.beginPath();
    for (let i=0;i<=500;i++) {
      const t=i/500*2*Math.PI/w;
      const xv=xFn(t,w,x0,v0), yv=xpFn(t,w,x0,v0);
      i===0 ? ctx.moveTo(px(xv),py(yv)) : ctx.lineTo(px(xv),py(yv));
    }
    ctx.stroke();

    // Direction arrows along ellipse
    for (let k=0;k<6;k++) {
      const t=(k/6)*2*Math.PI/w;
      const xv=xFn(t,w,x0,v0), yv=xpFn(t,w,x0,v0);
      const dt=0.01;
      const xv2=xFn(t+dt,w,x0,v0), yv2=xpFn(t+dt,w,x0,v0);
      const dx=px(xv2)-px(xv), dy=py(yv2)-py(yv);
      const len=Math.sqrt(dx*dx+dy*dy);
      if (len<1) continue;
      const sc=10/len;
      ctx.fillStyle=COL.phase;
      ctx.beginPath();
      const angle=Math.atan2(dy,dx);
      const hs=8;
      ctx.moveTo(px(xv)+dx*sc, py(yv)+dy*sc);
      ctx.lineTo(px(xv)+dx*sc-hs*Math.cos(angle-Math.PI/7),
                 py(yv)+dy*sc-hs*Math.sin(angle-Math.PI/7));
      ctx.lineTo(px(xv)+dx*sc-hs*Math.cos(angle+Math.PI/7),
                 py(yv)+dy*sc-hs*Math.sin(angle+Math.PI/7));
      ctx.closePath(); ctx.fill();
    }

    // Start point
    ctx.fillStyle='#e74c3c';
    ctx.beginPath(); ctx.arc(px(x0),py(v0),6,0,2*Math.PI); ctx.fill();
    ctx.fillStyle='#c0392b'; ctx.font='bold 11px Arial';
    ctx.fillText(`(x₀,v₀)=(${x0.toFixed(1)},${v0.toFixed(1)})`,px(x0)+8,py(v0)-6);

    // Axis labels
    ctx.fillStyle='#555'; ctx.font='12px Arial';
    ctx.fillText('x(t)', W-padR+2, py(0)+4);
    ctx.fillText("x'(t)", px(0)+4, padT-6);
    for (let v=-2;v<=2;v++) {
      const xv=v*rng/2;
      ctx.fillText(xv.toFixed(1), px(xv)-12, H-padB+15);
      ctx.fillText(xv.toFixed(1), padL-36, py(xv)+4);
    }

    // Semi-axis labels
    ctx.fillStyle=COL.phase; ctx.font='bold 11px Arial';
    ctx.fillText(`semi-axis a = A = ${A.toFixed(3)}`, px(A)+4, py(0)-6);
    ctx.fillText(`semi-axis b = Aω = ${Ap.toFixed(3)}`, px(0)+4, py(Ap)-6);

    ctx.fillStyle='#2c3e50'; ctx.font='bold 12px Arial';
    ctx.fillText('Phase portrait (x, x\') — closed ellipse', padL+10, padT+18);
  }

  // ── Formula and info cards ─────────────────────────────────────
  function updateFormula(w, x0, v0) {
    const A   = Math.sqrt(x0*x0+v0*v0/(w*w));
    const phi = Math.atan2(-v0/w, x0);
    const T   = 2*Math.PI/w;
    const f   = 1/T;
    const E   = 0.5*(v0*v0+w*w*x0*x0);

    const c2  = (v0/w).toFixed(3);
    document.getElementById('formulaBox').innerHTML =
      `<b>x(t)</b> = ${x0.toFixed(2)}·cos(${w.toFixed(2)}t) + ${c2}·sin(${w.toFixed(2)}t)`+
      `&nbsp;=&nbsp;<b>${A.toFixed(3)}·cos(${w.toFixed(2)}t + ${phi.toFixed(3)})</b><br>`+
      `<b>x'(t)</b> = ${(-x0*w).toFixed(3)}·sin(${w.toFixed(2)}t) + ${v0.toFixed(2)}·cos(${w.toFixed(2)}t)<br>`+
      `<b>x''(t)</b> = −${(w*w).toFixed(3)}·x(t)`;

    document.getElementById('infoGrid').innerHTML =
      `<div class="info-card"><b>${A.toFixed(4)}</b>Amplitude A</div>`+
      `<div class="info-card"><b>${T.toFixed(4)} s</b>Period T = 2π/ω</div>`+
      `<div class="info-card"><b>${f.toFixed(4)} Hz</b>Frequency f = 1/T</div>`+
      `<div class="info-card"><b>${E.toFixed(4)}</b>Total energy ½(v₀²+ω²x₀²)</div>`;
  }

  // ── Values table ──────────────────────────────────────────────
  function buildTable(w, x0, v0) {
    const T=2*Math.PI/w;
    const times=[0, T/4, T/2, 3*T/4, T, 1.5*T, 2*T];
    const tbody=document.getElementById('valBody');
    tbody.innerHTML='';
    for (const t of times) {
      const xv  = xFn(t,w,x0,v0);
      const xpv = xpFn(t,w,x0,v0);
      const xppv= xppFn(t,w,x0,v0);
      const E   = 0.5*(xpv*xpv+w*w*xv*xv);
      const tr=document.createElement('tr');
      tr.innerHTML=
        `<td>${t.toFixed(4)}</td>`+
        `<td>${xv.toFixed(6)}</td>`+
        `<td>${xpv.toFixed(6)}</td>`+
        `<td>${xppv.toFixed(6)}</td>`+
        `<td>${E.toFixed(6)}</td>`;
      tbody.appendChild(tr);
    }
  }

  // ── Legend ─────────────────────────────────────────────────────
  function updateLegend(deriv) {
    const items=[
      {col:COL.x,   lw:2.5, dash:false, label:'x(t) — displacement'},
      {col:COL.xp,  lw:1.8, dash:true,  label:"x'(t) — velocity"},
      {col:COL.xpp, lw:1.5, dash:true,  label:"x''(t) — acceleration"},
    ];
    const leg=document.getElementById('legend');
    leg.innerHTML=items.slice(0,deriv+1).map(it=>
      `<div class="leg-item">
        <span class="leg-swatch" style="background:${it.col};
          ${it.dash?'background: repeating-linear-gradient(90deg,'+it.col+' 0,'+it.col+' 5px,transparent 5px,transparent 9px)':''}">
        </span>${it.label}</div>`
    ).join('');
  }

  // ── Master draw ───────────────────────────────────────────────
  function draw() {
    const {w,x0,v0,nPer,deriv,showPhase}=getP();
    updateFormula(w,x0,v0);
    const T=2*Math.PI/w;
    drawMain(w,x0,v0,nPer,deriv);
    updateLegend(deriv);
    document.getElementById('phasePanel').style.display=showPhase?'block':'none';
    if (showPhase) drawPhase(w,x0,v0);
    buildTable(w,x0,v0);
  }

  draw();
</script>
</body>
</html>
```

> **How to use the application:**
> - **ω slider** — changes the angular frequency. Higher $\omega$ → shorter period, faster oscillation.
> - **x₀ slider** — sets the initial displacement (how far the spring is stretched at $t=0$).
> - **v₀ slider** — sets the initial velocity. Try $x_0=0, v_0>0$ for a pure sine wave.
> - **Periods slider** — how many full oscillations to display.
> - **Show derivatives slider** — toggle between showing $x(t)$ only, $x$ and $x'$, or all three curves.
> - **Phase portrait** — the $x'$ vs $x$ plot always traces a perfect ellipse, confirming undamped oscillation. The red dot marks the starting point $(x_0, v_0)$.
> - The **values table** shows $x$, $x'$, $x''$, and total energy at key fractions of the period. Notice the energy column is constant — energy is conserved.

---

## Summary

| Quantity | Expression |
|---|---|
| ODE | $x'' + \omega^2 x = 0$ |
| Characteristic roots | $\lambda = \pm i\omega$ |
| General solution | $x(t) = C_1\cos(\omega t) + C_2\sin(\omega t)$ |
| With initial conditions | $x(t) = x_0\cos(\omega t) + \frac{v_0}{\omega}\sin(\omega t)$ |
| First derivative | $x'(t) = -x_0\omega\sin(\omega t) + v_0\cos(\omega t)$ |
| Second derivative | $x''(t) = -\omega^2 x(t)$ |
| Amplitude | $A = \sqrt{x_0^2 + v_0^2/\omega^2}$ |
| Period | $T = 2\pi/\omega$ |
| Frequency | $f = \omega/(2\pi)$ |
| Total energy | $E = \frac{1}{2}(v_0^2 + \omega^2 x_0^2) = \frac{1}{2}\omega^2 A^2$ = const |
| Phase portrait | Ellipse with semi-axes $A$ and $A\omega$ |

---

## 5 Possible Questions & Answers

---

**Q1: Why does the characteristic equation $\lambda^2 + \omega^2 = 0$ give imaginary roots, and what does that imply about the solution?**

**A:** The equation $\lambda^2 = -\omega^2$ has no real solutions because a real number squared is always non-negative — it cannot equal $-\omega^2 < 0$. The solutions are therefore complex: $\lambda = \pm i\omega$. In general, complex roots $\lambda = \alpha \pm i\beta$ of a characteristic equation produce solutions of the form $e^{\alpha t}(C_1\cos(\beta t) + C_2\sin(\beta t))$. Here $\alpha = 0$ (no real part), so there is no exponential growth or decay — only pure oscillation at frequency $\beta = \omega$. If $\alpha \neq 0$, the oscillation would also grow ($\alpha > 0$) or decay ($\alpha < 0$), giving a **damped** or **unstable** oscillator.

---

**Q2: Show that the total mechanical energy $E = \frac{1}{2}[(x')^2 + \omega^2 x^2]$ is conserved.**

**A:** Differentiate $E$ with respect to time:
$$\frac{dE}{dt} = \frac{1}{2}\left[2x'x'' + 2\omega^2 x x'\right] = x'\left[x'' + \omega^2 x\right]$$
But $x'' + \omega^2 x = 0$ from the ODE, so:
$$\frac{dE}{dt} = x' \cdot 0 = 0$$
Therefore $E$ is constant for all $t$. Physically, this means the total energy (kinetic $\frac{1}{2}(x')^2$ plus potential $\frac{1}{2}\omega^2 x^2$, analogous to $\frac{1}{2}mv^2 + \frac{1}{2}kx^2$ for a spring) is perfectly conserved — there is no damping and no energy loss. In the phase portrait, this manifests as the trajectory tracing the same closed ellipse forever.

---

**Q3: What is the phase portrait of the harmonic oscillator and what does its shape tell us?**

**A:** The phase portrait plots $x'(t)$ (velocity) on the vertical axis against $x(t)$ (position) on the horizontal axis, with $t$ as a parameter. For the harmonic oscillator, the trajectory traces an **ellipse** with semi-axes $A$ (along $x$) and $A\omega$ (along $x'$). This ellipse is closed — the system returns to exactly the same state after every period $T$, confirming perfect periodic motion with no energy change. The shape encodes the ratio of kinetic to potential energy at each point: at the tips of the $x$-axis (maximum displacement) all energy is potential and $x' = 0$; at the tips of the $x'$-axis (equilibrium) all energy is kinetic and $x = 0$. If $\omega = 1$, the ellipse becomes a circle.

---

**Q4: How would the solution change if a damping term $2\gamma x'$ were added, giving $x'' + 2\gamma x' + \omega^2 x = 0$?**

**A:** The characteristic equation becomes $\lambda^2 + 2\gamma\lambda + \omega^2 = 0$, with roots $\lambda = -\gamma \pm \sqrt{\gamma^2 - \omega^2}$. Three cases arise: (1) **Underdamped** ($\gamma < \omega$): roots are complex $\lambda = -\gamma \pm i\sqrt{\omega^2-\gamma^2}$, giving $x(t) = e^{-\gamma t}(C_1\cos(\omega_d t) + C_2\sin(\omega_d t))$ where $\omega_d = \sqrt{\omega^2-\gamma^2}$ — an oscillation that decays exponentially. (2) **Critically damped** ($\gamma = \omega$): one repeated root $\lambda = -\gamma$, giving $x(t) = (C_1+C_2 t)e^{-\gamma t}$ — fastest possible return to equilibrium without oscillation. (3) **Overdamped** ($\gamma > \omega$): two distinct real roots, giving $x(t) = C_1 e^{\lambda_1 t} + C_2 e^{\lambda_2 t}$ — slow exponential return with no oscillation. In all damped cases, the phase portrait spirals inward rather than forming a closed ellipse.

---

**Q5: A spring-mass system has mass $m = 2$ kg and spring constant $k = 8$ N/m. It is released from $x_0 = 0.5$ m with zero initial velocity. Write the solution explicitly.**

**A:** For a spring-mass system, the equation of motion is $m\ddot{x} + kx = 0$, i.e. $\ddot{x} + \frac{k}{m}x = 0$. The angular frequency is:
$$\omega = \sqrt{\frac{k}{m}} = \sqrt{\frac{8}{2}} = \sqrt{4} = 2 \text{ rad/s}$$
With $x_0 = 0.5$, $v_0 = 0$:
$$C_1 = x_0 = 0.5, \qquad C_2 = \frac{v_0}{\omega} = 0$$
$$x(t) = 0.5\cos(2t) \text{ m}$$
The period is $T = 2\pi/2 = \pi \approx 3.14$ s, the amplitude is $A = 0.5$ m, and the maximum velocity (at $x = 0$) is $|x'|_{\max} = A\omega = 0.5 \times 2 = 1$ m/s. The total energy is $E = \frac{1}{2}k A^2 = \frac{1}{2}(8)(0.25) = 1$ J, constant throughout the motion.