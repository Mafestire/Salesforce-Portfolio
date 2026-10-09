<template>
  <div class="astro-bg" ref="bgRef">
    <!-- ================= CANVAS LAYER ================= -->
    <canvas ref="canvasRef" class="astro-canvas"></canvas>

    <!-- ================= DOM LAYER ================= -->

    <!-- 🌑 BIG GLASS RING (left) — STATIC -->
    <div class="main-ring-wrap" ref="mainRingRef">
      <div class="main-ring">
        <div class="ring-core"></div>
      </div>
    </div>
    <!-- 👆 main-ring-wrap closes HERE -->

    <!-- 🌐 Sphere #1 — Salesforce cloud -->
    <div
      class="orbit-node"
      ref="node1Ref"
      @mouseenter="pause('n1')"
      @mouseleave="resume('n1')"
    >
      <img
        src="https://i.postimg.cc/mhfjBzSr/Salesforce-Logo-removebg-preview.png"
        alt="Salesforce"
        class="node-img"
      />
    </div>

    <!-- 🌐 Sphere #2 — Trailhead badge -->
    <div
      class="orbit-node"
      ref="node2Ref"
      @mouseenter="pause('n2')"
      @mouseleave="resume('n2')"
    >
      <img
        src="https://i.postimg.cc/KjJTs1sR/Trailhead-Logo-removebg-preview.png"
        alt="Trailhead"
        class="node-img"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "AnimatedBackground",
  data() {
    return {
      stars: [],
      rafId: null,
      resizeObserver: null,
      // The far-right node travels around the big ellipse
      // Two orbit nodes — both ride the same ellipse around the big left ring
nodes: {
  n1: {
    cx: 0.50,   // center of ellipse — moved to middle
    cy: 0.50,   // vertical center
    rx: 0.40,   // horizontal radius — sweeps almost full width
    ry: 0.30,   // vertical radius — nice stretch up/down
    speed: 0.00035,
    phase: -0.60,  // starts top-right of the ring
    paused: false,
  },
  n2: {
    cx: 0.50,
    cy: 0.50,
    rx: 0.40,
    ry: 0.30,
    speed: 0.00035,
    phase: 0.60,   // starts bottom-right of the ring
    paused: false,
  },
},
    };
  },
  mounted() {
    this.setupCanvas();
    this.loop();
    this.resizeObserver = new ResizeObserver(() => this.setupCanvas());
    this.resizeObserver.observe(this.$refs.bgRef);
  },
  beforeUnmount() {
    cancelAnimationFrame(this.rafId);
    if (this.resizeObserver) this.resizeObserver.disconnect();
  },
  methods: {
    pause(id) { if (this.nodes[id]) this.nodes[id].paused = true; },
resume(id) { if (this.nodes[id]) this.nodes[id].paused = false; },

    /* ---------------------------------------------------------
       CANVAS SETUP — DPR-aware sizing + star generation
    --------------------------------------------------------- */
    setupCanvas() {
      const canvas = this.$refs.canvasRef;
      const wrap = this.$refs.bgRef;
      if (!canvas || !wrap) return;

      const dpr = window.devicePixelRatio || 1;
      const { width, height } = wrap.getBoundingClientRect();

      canvas.width = width * dpr;
      canvas.height = height * dpr;
      canvas.style.width = `${width}px`;
      canvas.style.height = `${height}px`;

      const ctx = canvas.getContext("2d");
      ctx.setTransform(dpr, 0, 0, dpr, 0, 0);

      this.generateStars(width, height);
    },

    generateStars(w, h) {
      // Low density — matches the sparse reference starfield
      const count = Math.floor((w * h) / 26000);
      this.stars = Array.from({ length: count }).map(() => ({
        x: Math.random() * w,
        y: Math.random() * h,
        r: Math.random() * 1.1 + 0.2,
        baseAlpha: Math.random() * 0.55 + 0.2,
        twinkleSpeed: Math.random() * 0.0012 + 0.0002,
        twinklePhase: Math.random() * Math.PI * 2,
      }));
    },

    /* ---------------------------------------------------------
       RENDER LOOP
    --------------------------------------------------------- */
    loop(t = 0) {
  this.drawFrame(t);
  this.updateNodes(t);
  this.rafId = requestAnimationFrame(this.loop.bind(this));
},
    /* ---------------------------------------------------------
       CANVAS DRAWING
    --------------------------------------------------------- */
    drawFrame(time) {
      const canvas = this.$refs.canvasRef;
      if (!canvas || !this.stars) return;
      const ctx = canvas.getContext("2d");
      const w = canvas.width / (window.devicePixelRatio || 1);
      const h = canvas.height / (window.devicePixelRatio || 1);

      // 1. Deep space gradient
      const bg = ctx.createLinearGradient(0, 0, 0, h);
      bg.addColorStop(0, "#050B14");
      bg.addColorStop(1, "#0A1325");
      ctx.fillStyle = bg;
      ctx.fillRect(0, 0, w, h);

      // 2. Milky nebula band — horizontal, centered, soft
      this.drawNebulaBand(ctx, w, h);

      // 3. Faint sketch orbits (thin "scratch" lines)
      this.drawSketchOrbits(ctx, w, h);

      // 4. Big sweeping ellipse + glowing tracer
      this.drawBigEllipse(ctx, w, h, time);

      // 5. Starfield (drawn last so stars sit on top of nebula)
      for (const s of this.stars) {
        const tw = 0.5 + 0.5 * Math.sin(time * s.twinkleSpeed + s.twinklePhase);
        ctx.globalAlpha = s.baseAlpha * (0.65 + 0.35 * tw);
        ctx.fillStyle = "#ffffff";
        ctx.beginPath();
        ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
        ctx.fill();
      }
      ctx.globalAlpha = 1;
    },

    /* Milky nebula — an elongated soft glow across the middle */
    drawNebulaBand(ctx, w, h) {
      ctx.save();
      // Main soft band
      const band = ctx.createRadialGradient(
        w * 0.55, h * 0.5, 0,
        w * 0.55, h * 0.5, Math.max(w, h) * 0.55
      );
      band.addColorStop(0, "rgba(140, 175, 230, 0.16)");
      band.addColorStop(0.35, "rgba(90, 130, 200, 0.10)");
      band.addColorStop(1, "rgba(5, 11, 20, 0)");
      ctx.fillStyle = band;

      // Squash the band horizontally so it reads as a milky strip
      ctx.beginPath();
      ctx.ellipse(w * 0.55, h * 0.5, w * 0.42, h * 0.18, 0, 0, Math.PI * 2);
      ctx.fill();

      // Brighter core (galactic center)
      const core = ctx.createRadialGradient(
        w * 0.58, h * 0.5, 0,
        w * 0.58, h * 0.5, w * 0.22
      );
      core.addColorStop(0, "rgba(190, 210, 240, 0.18)");
      core.addColorStop(1, "rgba(90, 130, 200, 0)");
      ctx.fillStyle = core;
      ctx.beginPath();
      ctx.ellipse(w * 0.58, h * 0.5, w * 0.22, h * 0.11, 0, 0, Math.PI * 2);
      ctx.fill();
      ctx.restore();
    },

    /* Faint thin sketch orbits — the "pencil lines" from the reference */
    drawSketchOrbits(ctx, w, h) {
      ctx.save();
      ctx.strokeStyle = "rgba(180, 210, 255, 0.10)";
      ctx.lineWidth = 0.8;

      // Left cluster: orbits around the big ring center
      const lx = w * 0.23;
      const ly = h * 0.5;
      for (let i = 0; i < 5; i++) {
        const rx = w * (0.05 + i * 0.045);
        const ry = h * (0.10 + i * 0.09);
        const rot = (i - 2) * 0.22;
        ctx.beginPath();
        ctx.ellipse(lx, ly, rx, ry, rot, 0, Math.PI * 2);
        ctx.stroke();
      }

      // Right cluster: orbits around the far-right node path
      const rx2 = w * 0.78;
      const ry2 = h * 0.5;
      for (let i = 0; i < 3; i++) {
        const rrx = w * (0.06 + i * 0.05);
        const rry = h * (0.08 + i * 0.08);
        const rot = (i - 1) * 0.3;
        ctx.beginPath();
        ctx.ellipse(rx2, ry2, rrx, rry, rot, 0, Math.PI * 2);
        ctx.stroke();
      }
      ctx.restore();
    },

    /* The BIG sweeping ellipse tying the left ring to the far-right node */
    drawBigEllipse(ctx, w, h, time) {
      const cx = w * this.nodes.n1.cx;
      const cy = h * this.nodes.n1.cy;
      const rx = w * this.nodes.n1.rx;
      const ry = h * this.nodes.n1.ry;

      ctx.save();

      // Outer soft glow pass
      ctx.strokeStyle = "rgba(150, 200, 255, 0.10)";
      ctx.lineWidth = 8;
      ctx.beginPath();
      ctx.ellipse(cx, cy, rx, ry, 0, 0, Math.PI * 2);
      ctx.stroke();

      // Main crisp line
      ctx.strokeStyle = "rgba(180, 215, 255, 0.42)";
      ctx.lineWidth = 1.2;
      ctx.beginPath();
      ctx.ellipse(cx, cy, rx, ry, 0, 0, Math.PI * 2);
      ctx.stroke();

      // Bright glowing tracer that rides the ellipse
const angle = time * this.nodes.n1.speed * 2 + this.nodes.n1.phase;
      const tx = cx + Math.cos(angle) * rx;
      const ty = cy + Math.sin(angle) * ry;
      const glow = ctx.createRadialGradient(tx, ty, 0, tx, ty, 60);
      glow.addColorStop(0, "rgba(220, 235, 255, 0.85)");
      glow.addColorStop(0.4, "rgba(140, 195, 255, 0.35)");
      glow.addColorStop(1, "rgba(100, 180, 255, 0)");
      ctx.fillStyle = glow;
      ctx.beginPath();
      ctx.arc(tx, ty, 60, 0, Math.PI * 2);
      ctx.fill();

      // Bright inner core of the tracer
      ctx.fillStyle = "rgba(255, 255, 255, 0.95)";
      ctx.beginPath();
      ctx.arc(tx, ty, 2.2, 0, Math.PI * 2);
      ctx.fill();

      ctx.restore();
    },

    /* Move the far-right DOM node along the big ellipse */
    updateNodes(time) {
  const wrap = this.$refs.bgRef;
  if (!wrap) return;

  let { width: w, height: h } = wrap.getBoundingClientRect();
  if (!w || !h) {
    w = window.innerWidth;
    h = window.innerHeight;
  }

  const pairs = [
    ["n1", this.$refs.node1Ref],
    ["n2", this.$refs.node2Ref],
  ];

  for (const [id, el] of pairs) {
    if (!el) continue;
    const o = this.nodes[id];
    if (o.paused) continue;

    const angle = time * o.speed * 2 + o.phase;
    const x = w * o.cx + Math.cos(angle) * w * o.rx;
    const y = h * o.cy + Math.sin(angle) * h * o.ry;

    el.style.transform = `translate3d(${x}px, ${y}px, 0) translate(-50%, -50%)`;
  }
},
  },
};
</script>

<style scoped lang="scss">
/* =========================================================
   ROOT WRAPPER
========================================================= */
.astro-bg {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
  z-index: 0;
  pointer-events: none;
  background: #050b14;
}

.astro-canvas {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  display: block;
}

/* =========================================================
   BIG GLASS RING (left) — thick torus, glowing
========================================================= */
.main-ring-wrap {
  position: absolute;
  top: 50%;
  left: 23%;               /* matches ellipse center on the left */
  width: 34rem;            /* outer diameter */
  height: 34rem;
  transform: translate(-50%, -50%);
  pointer-events: auto;
}

.main-ring {
  position: relative;
  width: 100%;
  height: 100%;
  border-radius: 50%;

  /* Thick glass torus look */
  background: radial-gradient(
    circle at 50% 50%,
    rgba(15, 25, 45, 0.55) 0%,
    rgba(20, 35, 60, 0.35) 55%,
    rgba(120, 170, 230, 0.18) 72%,
    rgba(180, 220, 255, 0.28) 82%,
    rgba(120, 170, 230, 0.10) 92%,
    rgba(15, 25, 45, 0) 100%
  );

  border: 1px solid rgba(180, 220, 255, 0.35);

  box-shadow:
    0 0 60px rgba(120, 180, 255, 0.28),
    0 0 140px rgba(80, 140, 220, 0.15),
    inset 0 0 80px rgba(140, 190, 255, 0.10),
    inset 0 0 20px rgba(200, 225, 255, 0.15);

  backdrop-filter: blur(3px);
  -webkit-backdrop-filter: blur(3px);
  animation: ringPulse 7s ease-in-out infinite;
}

/* Tiny glow dot at ring center (reference has this) */
.ring-core {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 14px;
  height: 14px;
  transform: translate(-50%, -50%);
  border-radius: 50%;
  background: radial-gradient(
    circle,
    rgba(255, 255, 255, 0.95) 0%,
    rgba(180, 220, 255, 0.6) 40%,
    rgba(120, 180, 255, 0) 100%
  );
  box-shadow: 0 0 22px rgba(180, 220, 255, 0.6);
}

/* Optional profile image inside the ring */
.main-profile-img {
  position: absolute;
  inset: 12%;
  width: 76%;
  height: 50%;
  object-fit: contain;
  border-radius: 50%;
  filter: drop-shadow(0 0 24px rgba(120, 180, 255, 0.5));
}

@keyframes ringPulse {
  0%, 100% {
    box-shadow:
      0 0 60px rgba(120, 180, 255, 0.28),
      0 0 140px rgba(80, 140, 220, 0.15),
      inset 0 0 80px rgba(140, 190, 255, 0.10),
      inset 0 0 20px rgba(200, 225, 255, 0.15);
  }
  50% {
    box-shadow:
      0 0 80px rgba(140, 195, 255, 0.42),
      0 0 180px rgba(90, 150, 230, 0.22),
      inset 0 0 100px rgba(150, 200, 255, 0.16),
      inset 0 0 26px rgba(210, 235, 255, 0.22);
  }
}

/* =========================================================
   ATTACHED SPHERES (top-right & bottom-right of big ring)
========================================================= */
.attached-node {
  position: absolute;
  width: 7rem;
  height: 7rem;
  border-radius: 50%;
  pointer-events: auto;
  cursor: pointer;

  background: radial-gradient(
    circle at 35% 30%,
    rgba(200, 225, 255, 0.35) 0%,
    rgba(120, 170, 225, 0.22) 40%,
    rgba(30, 50, 85, 0.35) 75%,
    rgba(15, 25, 45, 0.2) 100%
  );
  border: 1px solid rgba(200, 225, 255, 0.55);
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);

  box-shadow:
    0 0 30px rgba(150, 200, 255, 0.5),
    0 0 70px rgba(100, 160, 235, 0.3),
    inset 0 0 30px rgba(180, 220, 255, 0.15),
    inset 0 -8px 20px rgba(0, 0, 0, 0.25);

  display: flex;
  align-items: center;
  justify-content: center;
  transition: box-shadow 0.35s ease, border-color 0.35s ease;
  animation: nodePulse 5s ease-in-out infinite;
}

.attached-node:hover {
  border-color: rgba(220, 240, 255, 0.95);
  box-shadow:
    0 0 45px rgba(180, 220, 255, 0.85),
    0 0 100px rgba(120, 180, 245, 0.5),
    inset 0 0 40px rgba(190, 225, 255, 0.25),
    inset 0 -8px 22px rgba(0, 0, 0, 0.3);
}

/* Top-right of big ring (~1 o'clock) */
.attached-node--top {
  top: -3.5rem;
  right: -1rem;
}

/* Bottom-right of big ring (~5 o'clock) */
.attached-node--bottom {
  bottom: -3.5rem;
  right: -1rem;
}

@keyframes nodePulse {
  0%, 100% {
    box-shadow:
      0 0 30px rgba(150, 200, 255, 0.5),
      0 0 70px rgba(100, 160, 235, 0.3),
      inset 0 0 30px rgba(180, 220, 255, 0.15),
      inset 0 -8px 20px rgba(0, 0, 0, 0.25);
  }
  50% {
    box-shadow:
      0 0 42px rgba(180, 215, 255, 0.72),
      0 0 95px rgba(120, 180, 245, 0.42),
      inset 0 0 38px rgba(200, 230, 255, 0.22),
      inset 0 -8px 22px rgba(0, 0, 0, 0.28);
  }
}

/* =========================================================
   FAR-RIGHT ORBIT NODE (travels along the big ellipse)
========================================================= */
.orbit-node {
  position: absolute;
  top: 0;
  left: 0;
  width: 7rem;
  height: 7rem;
  border-radius: 50%;
  pointer-events: auto;
  cursor: pointer;
  will-change: transform;

  background: radial-gradient(
    circle at 35% 30%,
    rgba(200, 225, 255, 0.35) 0%,
    rgba(120, 170, 225, 0.22) 40%,
    rgba(30, 50, 85, 0.35) 75%,
    rgba(15, 25, 45, 0.2) 100%
  );
  border: 1px solid rgba(200, 225, 255, 0.55);
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);

  box-shadow:
    0 0 30px rgba(150, 200, 255, 0.5),
    0 0 70px rgba(100, 160, 235, 0.3),
    inset 0 0 30px rgba(180, 220, 255, 0.15),
    inset 0 -8px 20px rgba(0, 0, 0, 0.25);

  display: flex;
  align-items: center;
  justify-content: center;
  transition: box-shadow 0.35s ease, border-color 0.35s ease;
}

.orbit-node:hover {
  border-color: rgba(220, 240, 255, 0.95);
  box-shadow:
    0 0 45px rgba(180, 220, 255, 0.85),
    0 0 100px rgba(120, 180, 245, 0.5),
    inset 0 0 40px rgba(190, 225, 255, 0.25),
    inset 0 -8px 22px rgba(0, 0, 0, 0.3);
}

/* Logo / image inside the spheres */
.node-img {
  width: 62%;
  height: 62%;
  object-fit: contain;
  filter: drop-shadow(0 0 8px rgba(180, 220, 255, 0.5));
  pointer-events: none;
}

/* =========================================================
   RESPONSIVE
========================================================= */
@media (max-width: 1280px) {
  .main-ring-wrap {
    width: 26rem;
    height: 26rem;
    left: 14%;
  }
  .attached-node,
  .orbit-node {
    width: 5.5rem;
    height: 5.5rem;
  }
  .attached-node--top,
  .attached-node--bottom {
    right: -0.75rem;
  }
  .attached-node--top { top: -2.75rem; }
  .attached-node--bottom { bottom: -2.75rem; }
}

@media (max-width: 1024px) {
  .main-ring-wrap {
    width: 20rem;
    height: 20rem;
    left: 12%;
  }
  .attached-node,
  .orbit-node {
    width: 4.5rem;
    height: 4.5rem;
  }
  .attached-node--top,
  .attached-node--bottom {
    right: -0.6rem;
  }
  .attached-node--top { top: -2.25rem; }
  .attached-node--bottom { bottom: -2.25rem; }
}

@media (max-width: 766px) {
  /* On mobile the ring fades into a subtle backdrop */
  .main-ring-wrap {
    left: 50%;
    top: 40%;
    width: 16rem;
    height: 16rem;
    opacity: 0.4;
  }
  .attached-node,
  .orbit-node {
    width: 3.5rem;
    height: 3.5rem;
    opacity: 0.55;
  }
}
</style>