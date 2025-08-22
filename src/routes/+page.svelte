<script>
  import { onMount } from "svelte";

  let canvas;

  onMount(() => {
    const ctx = canvas.getContext("2d");
    const stars = Array.from({ length: 150 }, () => ({
      x: Math.random() * window.innerWidth,
      y: Math.random() * window.innerHeight,
      r: Math.random() * 1.5,
      a: Math.random()
    }));

    function draw() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      ctx.fillStyle = "black";
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      for (const s of stars) {
        ctx.beginPath();
        ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
        ctx.fillStyle = `rgba(255,255,255,${s.a})`;
        ctx.fill();
      }
      requestAnimationFrame(draw);
    }

    function resize() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }

    window.addEventListener("resize", resize);
    resize();
    draw();
  });

</script>

<canvas bind:this={canvas}></canvas>

<div class="content">
  <header>
    <img src="/logo.svg" alt="stOLAS" sizes="400px" />
  </header>

  <main>
    <h1>Soon.</h1>
  </main>

  <footer>
    © stOLAS 2025
  </footer>
</div>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');

  body {
    font-family: 'Figtree', system-ui, sans-serif;
  }
  canvas {
    position: fixed;
    inset: 0;
    width: 100%;
    height: 100%;
    z-index: 0;
  }
  .content {
    position: relative;
    z-index: 1;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    color: #d7e2ea;
    text-align: center;
    font-family: system-ui, sans-serif;
  }
  header {
    padding: 2rem 0;
  }
  header img {
    height: 132px;
  }
  main {
    flex: 1;
    display: flex;
    align-items: center;
  }
  footer {
    padding: 2rem 0;
    font-size: 12px;
    opacity: 0.7;
  }
  h1 {
      font-size: clamp(48px, 10vw, 96px);
      font-weight: 600;
      background: linear-gradient(180deg, #FFF 0%, #AFD2E4 100%);
      background-clip: text;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
  }

</style>
