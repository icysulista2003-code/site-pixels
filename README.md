<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Million Pixels Homepage</title>
<style>
  * {
    box-sizing: border-box;
    margin: 0; padding: 0;
  }
  body {
    font-family: Arial, sans-serif;
    background: #f0f0f0;
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    color: #222;
  }
  header, footer {
    background: #222;
    color: #fff;
    text-align: center;
    padding: 16px 10px;
    user-select: none;
  }
  header {
    font-weight: bold;
    font-size: 1.2rem;
  }
  main {
    flex-grow: 1;
    padding: 20px;
    display: flex;
    justify-content: center;
    overflow-x: auto;
  }
  #pixel-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(20px, 1fr));
    gap: 4px;
    max-width: 100%;
    background: #fff;
    padding: 12px;
    border: 3px solid #222;
    box-shadow: 0 0 15px rgba(0,0,0,0.3);
    user-select: none;
  }
  .pixel {
    width: 20px;
    height: 20px;
    background-color: #e63946; /* cor vibrante clássica */
    border: 1px solid #b22234;
    box-shadow:
      inset 0 0 3px rgba(255,255,255,0.5),
      inset 0 -2px 2px rgba(0,0,0,0.3);
    cursor: default;
    flex-shrink: 0;
  }
  /* Responsividade */
  @media (max-width: 600px) {
    .pixel {
      width: 15px;
      height: 15px;
    }
  }
</style>
</head>
<body>
  <header>
    MILLION PIXELS HOMEPAGE
  </header>
  <main>
    <div id="pixel-grid"></div>
  </main>
  <footer>
    © 2025 - Seu Site de Pixels
  </footer>

<script>
  const grid = document.getElementById('pixel-grid');
  const totalPixels = 2000;

  for (let i = 0; i < totalPixels; i++) {
    const pixel = document.createElement('div');
    pixel.className = 'pixel';
    grid.appendChild(pixel);
  }
</script>
</body>
</html>
