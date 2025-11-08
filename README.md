# gh0st-creator.github.io
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Diseñador Metal–Ligando</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap" rel="stylesheet">
  <style>
    /* === ESTILO GLOBAL === */
    :root {
      --primary: #1a73e8;
      --secondary: #5f6368;
      --background: #fafafa;
      --card-bg: #ffffff;
      --border: #dadce0;
      --accent: #e8f0fe;
      --radius: 12px;
    }

    * {
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', sans-serif;
      background-color: var(--background);
      color: #202124;
      padding: 40px;
      line-height: 1.5;
      max-width: 900px;
      margin: 0 auto;
    }

    h1 {
      font-size: 28px;
      color: var(--primary);
      margin-bottom: 10px;
    }

    h2 {
      margin-top: 40px;
      font-size: 20px;
      color: var(--secondary);
    }

    .section {
      margin-top: 10px;
    }

    /* === GRILLAS Y TARJETAS === */
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
      gap: 16px;
      margin-top: 10px;
    }

    .card {
      background: var(--card-bg);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 16px;
      text-align: center;
      cursor: pointer;
      transition: all 0.2s ease;
      box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05);
    }

    .card:hover {
      background-color: var(--accent);
      transform: translateY(-2px);
    }

    .card.active {
      background-color: var(--primary);
      color: white;
      font-weight: 600;
      border-color: var(--primary);
    }

    .icon {
      font-size: 28px;
      margin-bottom: 8px;
      display: block;
    }

    /* === SECCIÓN DE RESULTADO === */
    .output {
      border: 2px dashed var(--border);
      background-color: #fff;
      border-radius: var(--radius);
      padding: 24px;
      margin-top: 16px;
      min-height: 100px;
      text-align: center;
      font-size: 16px;
    }

    .compound {
      font-weight: 600;
      color: var(--primary);
    }

    footer {
      margin-top: 60px;
      text-align: center;
      font-size: 13px;
      color: #777;
    }
  </style>
</head>
<body>

  <h1>🔬 Diseñador Metal–Ligando</h1>
  <p>Selecciona un metal y un ligando para explorar posibles combinaciones y ejemplos análogos.</p>

  <!-- SECCIÓN 1 -->
  <div class="section">
    <h2>⚙️ 1. Selecciona un metal</h2>
    <div class="grid" id="metales">
      <div class="card"><span class="icon">🧲</span>Eu³⁺</div>
      <div class="card"><span class="icon">⚛️</span>Tb³⁺</div>
      <div class="card"><span class="icon">🌕</span>Ir</div>
      <div class="card"><span class="icon">💠</span>Ru</div>
      <div class="card"><span class="icon">🔩</span>Mn</div>
    </div>
  </div>

  <!-- SECCIÓN 2 -->
  <div class="section">
    <h2>🧪 2. Selecciona un ligando</h2>
    <div class="grid" id="ligandos">
      <div class="card"><span class="icon">💫</span>bipiridina</div>
      <div class="card"><span class="icon">🌀</span>porfirina</div>
      <div class="card"><span class="icon">🧴</span>acac</div>
      <div class="card"><span class="icon">☀️</span>Cp*</div>
      <div class="card"><span class="icon">🌫️</span>CO</div>
    </div>
  </div>

  <!-- SECCIÓN 3 -->
  <div class="section">
    <h2>🔍 3. Compuestos análogos multifuncionales</h2>
    <div class="output" id="resultado">
      <p>Selecciona un metal y un ligando para ver ejemplos.</p>
    </div>
  </div>

  <footer>
    © 2025 | Proyecto de Química de Coordinación – Presentación de Clase
  </footer>

  <script>
    const metals = document.querySelectorAll('#metales .card');
    const ligands = document.querySelectorAll('#ligandos .card');
    const resultado = document.getElementById('resultado');
    let selectedMetal = null;
    let selectedLigand = null;

    function updateSelection(type, element) {
      const group = type === 'metal' ? metals : ligands;
      group.forEach(c => c.classList.remove('active'));
      element.classList.add('active');

      if (type === 'metal') selectedMetal = element.textContent.trim();
      else selectedLigand = element.textContent.trim();

      if (selectedMetal && selectedLigand) {
        resultado.innerHTML = `
          <p><b>Selección:</b> ${selectedMetal} + ${selectedLigand}</p>
          <p>Ejemplo: <span class="compound">${selectedMetal}(${selectedLigand})₃</span></p>
          <p>Estos complejos presentan propiedades ópticas y electrónicas interesantes, útiles en catálisis o luminiscencia.</p>
        `;
      }
    }

    metals.forEach(card => card.addEventListener('click', () => updateSelection('metal', card)));
    ligands.forEach(card => card.addEventListener('click', () => updateSelection('ligand', card)));
  </script>

</body>
</html>
