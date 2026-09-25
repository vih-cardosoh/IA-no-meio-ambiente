<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>IA no Meio Ambiente - Fluxograma</title>
  
  <!-- Importação da biblioteca Mermaid.js para o fluxograma -->
  <script type="module">
    import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.mmin.mjs';
    mermaid.initialize({ 
      startOnLoad: true, 
      theme: 'forest',
      flowchart: { curve: 'basis' }
    });
  </script>

  <!-- Estilos CSS unificados -->
  <style>
    :root {
      --primary: #2d6a4f;
      --secondary: #52b788;
      --background: #f4f9f4;
      --card-bg: #ffffff;
      --text: #1b4332;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background-color: var(--background);
      color: var(--text);
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }

    header {
      background-color: var(--primary);
      color: white;
      text-align: center;
      padding: 2.5rem 1rem;
    }

    header h1 {
      font-size: 2.2rem;
      margin-bottom: 0.5rem;
    }

    header p {
      font-size: 1.1rem;
      opacity: 0.9;
    }

    .container {
      max-width: 1100px;
      margin: 2rem auto;
      padding: 0 1rem;
      flex: 1;
    }

    .card {
      background: var(--card-bg);
      border-radius: 12px;
      padding: 1.5rem;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
      margin-bottom: 2rem;
    }

    .flowchart-card {
      text-align: center;
      overflow-x: auto;
    }

    .flowchart-card h2 {
      margin-bottom: 1.5rem;
      color: var(--primary);
    }

    .grid-details {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 1.5rem;
    }

    .grid-details .card h3 {
      color: var(--primary);
      margin-bottom: 0.5rem;
    }

    .grid-details .card p {
      color: #555;
      line-height: 1.5;
      font-size: 0.95rem;
    }

    footer {
      text-align: center;
      padding: 1.5rem;
      background-color: var(--primary);
      color: white;
      font-size: 0.9rem;
      margin-top: auto;
    }
  </style>
</head>
<body>

  <header>
    <h1>🌱 Como a IA Ajuda no Meio Ambiente</h1>
    <p>Um fluxo interativo do impacto da tecnologia na sustentabilidade do planeta</p>
  </header>

  <main class="container">
    <section class="card flowchart-card">
      <h2>Fluxograma de Aplicação</h2>
      <div class="mermaid">
        graph TD
          A[Coleta de Dados Ambientais] -->|Sensores, Satélites e IoT| B(Processamento por Modelos de IA)
          
          B --> C[Monitoramento Florestal]
          B --> D[Gestão de Energia]
          B --> E[Agricultura de Precisão]
          B --> F[Previsão Climática]

          C --> C1[Detecção de Desmatamento e Queimadas]
          C1 --> C2[Envio de Alertas em Tempo Real para Autoridades]

          D --> D1[Otimização de Redes Elétricas e Renováveis]
          D1 --> D2[Redução de Pegada de Carbono e Desperdício]

          E --> E1[Uso Eficiente de Água e Fertilizantes]
          E1 --> E2[Preservação do Solo e Menos Poluição]

          F --> F1[Previsão de Enchentes e Eventos Extremos]
          F1 --> F2[Ações Preventivas e Proteção de Biodiversidade]

          C2 --> G([Planeta Mais Sustentável])
          D2 --> G
          E2 --> G
          F2 --> G
      </div>
    </section>

    <section class="grid-details">
      <div class="card">
        <h3>🌳 Monitoramento Florestal</h3>
        <p>A IA analisa imagens de satélite para identificar focos de incêndio e desmatamento ilegal antes que se espalhem.</p>
      </div>
      <div class="card">
        <h3>⚡ Gestão Energética</h3>
        <p>Algoritmos preveem picos de demanda e otimizam a distribuição de energia eólica e solar.</p>
      </div>
      <div class="card">
        <h3>🌾 Agricultura Inteligente</h3>
        <p>Aplica insumos agrícolas apenas nas áreas necessárias, reduzindo o desperdício de água e contaminação do solo.</p>
      </div>
      <div class="card">
        <h3>⛈️ Clima e Desastres</h3>
        <p>Modelos preditivos alertam comunidades sobre enchentes e tempestades com maior antecedência.</p>
      </div>
    </section>
  </main>

  <footer>
    <p>Projeto em arquivo único • HTML, CSS e JS unificados</p>
  </footer>

</body>
</html>
