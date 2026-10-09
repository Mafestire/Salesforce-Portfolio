<template>
  <div class="space-bg" ref="bgRef">
    <canvas ref="canvasRef" class="space-canvas"></canvas>
  </div>
</template>

<script>
export default {
  name: "SpaceBackground",
  data() {
    return {
      stars: [],
      rafId: null,
      resizeObserver: null,
    };
  },
  mounted() {
    this.setupCanvas();
    this.loop();
    this.resizeObserver = new ResizeObserver(() => this.setupCanvas());
    this.resizeObserver.observe(this.$refs.bgRef);
    window.addEventListener("resize", this.setupCanvas);
    this.$nextTick(() => this.setupCanvas());
    setTimeout(() => this.setupCanvas(), 250);
  },
  beforeUnmount() {
    cancelAnimationFrame(this.rafId);
    if (this.resizeObserver) this.resizeObserver.disconnect();
    window.removeEventListener("resize", this.setupCanvas);
  },
  methods: {
    setupCanvas() {
      const canvas = this.$refs.canvasRef;
      const wrap = this.$refs.bgRef;
      if (!canvas || !wrap) return;

      const dpr = window.devicePixelRatio || 1;
      let { width, height } = wrap.getBoundingClientRect();
      if (!width || !height) {
        width = window.innerWidth;
        height = window.innerHeight;
      }

      canvas.width = width * dpr;
      canvas.height = height * dpr;
      canvas.style.width = `${width}px`;
      canvas.style.height = `${height}px`;

      const ctx = canvas.getContext("2d");
      ctx.setTransform(dpr, 0, 0, dpr, 0, 0);

      this.generateStars(width, height);
    },

    generateStars(w, h) {
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

    loop(t = 0) {
      this.drawFrame(t);
      this.rafId = requestAnimationFrame(this.loop.bind(this));
    },

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

      // 2. Milky nebula band
      // this.drawNebulaBand(ctx, w, h);

      // 3. Faint sketch orbits (thin "scratch" lines)
      this.drawSketchOrbits(ctx, w, h);

      // 3. Starfield
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

    drawNebulaBand(ctx, w, h) {
      ctx.save();
      const band = ctx.createRadialGradient(
        w * 0.55, h * 0.5, 0,
        w * 0.55, h * 0.5, Math.max(w, h) * 0.55
      );
      band.addColorStop(0, "rgba(140, 175, 230, 0.16)");
      band.addColorStop(0.35, "rgba(90, 130, 200, 0.10)");
      band.addColorStop(1, "rgba(5, 11, 20, 0)");
      ctx.fillStyle = band;
      ctx.beginPath();
      ctx.ellipse(w * 0.55, h * 0.5, w * 0.42, h * 0.18, 0, 0, Math.PI * 2);
      ctx.fill();

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
    }

  },
};
</script>

<style scoped lang="scss">
.space-bg {
  position: fixed;
  inset: 0;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  z-index: -1;
  pointer-events: none;
  background: #050b14;
}

.space-canvas {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  display: block;
}
</style>