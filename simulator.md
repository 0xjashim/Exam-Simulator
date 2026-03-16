---
layout: page
title: Simulator
permalink: /simulator/
---

<div class="simulator-wrap">
  <div class="simulator-titlebar">
    <div style="display:flex;align-items:center;gap:10px;">
      <div class="sim-dots">
        <span class="sim-dot r"></span>
        <span class="sim-dot y"></span>
        <span class="sim-dot g"></span>
      </div>
      <span style="color:#4a7a4a;font-size:12px;letter-spacing:1px;">exam-simulator.exe</span>
    </div>
    <span class="sim-status">RUNNING</span>
  </div>
  <div id="sim-root">
    {% include simulator.html %}
  </div>
</div>

<style>
/* Hide the simulator's own banner — page title serves that purpose */
#sim-root .top-banner { display: none !important; }

/* Blend simulator colours with Minima dark theme */
#sim-root {
  --bg: #0d0f14;
  --surface: #0a1a0a;
  --surface2: #0f200f;
  --border: #00ff4122;
  --accent: #00ff41;
  --accent2: #00aa2a;
  --correct: #00ff41;
  --wrong: #ff0040;
  --warn: #ffb300;
  --text: #c9d1d9;
  --muted: #4a7a4a;
  --font-head: 'Courier New', monospace;
  --font-mono: 'Courier New', monospace;
}

#sim-root #app {
  max-width: 100%;
  padding: 1.5rem;
}
</style>
