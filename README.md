<!DOCTYPE html>
<html lang="pt-PT">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Painel Interativo: IA e Sustentabilidade</title>
  <style>
    :root {
      --bg-color: #0f172a;
      --card-bg: #1e293b;
      --accent-green: #10b981;
      --accent-blue: #3b82f6;
      --text-main: #f8fafc;
      --text-muted: #94a3b8;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', system-ui, sans-serif;
    }

    body {
      background-color: var(--bg-color);
      color: var(--text-main);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    header {
      padding: 2rem 1rem;
      text-align: center;
      background: linear-gradient(180deg, #162e2b 0%, var(--bg-color) 100%);
      border-bottom: 1px solid #334155;
    }

    header h1 {
      color: var(--accent-green);
      font-size: 2rem;
      margin-bottom: 0.5rem;
    }

    header p {
      color: var(--text-muted);
    }

    .main-container {
      max-width: 1200px;
      margin: 2rem auto;
      padding: 0 1rem;
      display: grid;
      grid-template-columns: 1fr 350px;
      gap: 2rem;
      flex: 1;
    }

    @media (max-width: 900px) {
      .main-container {
        grid-template-columns: 1fr;
      }
    }

    /* Fluxograma Interativo em Canvas / DOM */
    .flowchart-container {
      background: var(--card-bg);
      border-radius: 12px;
      padding: 1.5rem;
      border: 1px solid #334155;
      display: flex;
      flex-direction: column;
      gap: 1.5rem;
    }

    .node-group {
      display: flex;
      justify-content: space-around;
      gap: 1rem;
      flex-wrap: wrap;
    }

    .node {
      background: #0f172a;
      border: 2px solid var(--accent-blue);
      border-radius: 8px;
      padding: 1rem;
      width: 200px;
      text-align: center;
      cursor: pointer;
      transition: all 0.3s ease;
      position: relative;
    }

    .node:hover {
      transform: translateY(-5px);
      border-color: var(--accent-green);
      box-shadow: 0 0 15px rgba(16, 185, 129, 0.3);
    }

    .node.active {
      border-color: var(--accent-green);
      background: #064e3b;
    }

    .node-root {
      border-color: #f59e0b;
      margin: 0 auto;
    }

    .arrow-down {
      text-align: center;
      color: var(--text-muted);
      font-size: 1.5rem;
    }

    /* Painel Lateral de Impacto */
    .sidebar {
      background: var(--card-bg);
      border-radius: 12px;
      padding: 1.5rem;
      border: 1px solid #334155;
      display: flex;
      flex-direction: column;
      gap: 1.5rem;
    }

    .metric-box {
      background: #0f172a;
      padding: 1rem;
      border-radius: 8px;
      border-left: 4px solid var(--accent-green);
    }

    .metric-value {
      font-size: 1.8rem;
      font-weight: bold;
      color: var(--accent-green);
    }

    .btn-simular {
      background: var(--accent-green);
      color: #000;
      font-weight: bold;
      border: none;
      padding: 1rem;
      border-radius: 8px;
      cursor: pointer;
      transition: opacity 0.2s;
    }

    .btn-simular:hover {
      opacity: 0.9;
    }

    footer {
      text-align: center;
      padding: 1.5rem;
      border-top: 1px solid #334155;
      color: var(--text-muted);
      font-size: 0.85rem;
    }
  </style>
</head>
<body>

  <header>
    <h1>🌍 EcoIA: Simulação de Impacto Ambiental</h1>
    <p>Clique nos blocos do fluxo para analisar cada solução tecnológica</p>
  </header>

  <main class="main-container">
    <section class="flowchart-container">
      <h2>Fluxo de Soluções Inteligentes</h2>
      
      <!-- Nó Principal -->
      <div class="node-group">
        <div class="node node-root" onclick="selecionarNo('root')">
          ⚡ <strong>Captação de Dados</strong>
          <p style="font-size: 0.75rem; color: var(--text-muted); margin-top: 4px;">Satélites & Sensores IoT</p>
        </div>
      </div>

      <div class="arrow-down">↓</div>

      <!-- Camada Intermédia -->
      <div class="node-group">
        <div class="node" id="node-florestas" onclick="selecionarNo('florestas')">
          🌲 <strong>Proteção Florestal</strong>
        </div>
        <div class="node" id="node-energia" onclick="selecionarNo('energia')">
          💡 <strong>Rede Elétrica</strong>
        </div>
        <div class="node" id="node-oceanos" onclick="selecionarNo('oceanos')">
          🌊 <strong>Limpeza Oceânica</strong>
        </div>
      </div>

      <div class="arrow-down">↓</div>

      <!-- Camada de Impacto -->
      <div class="node-group">
        <div class="node" id="node-resultado" style="width: 100%; border-color: var(--accent-green);">
          🎯 <strong id="resultado-titulo">Selecione uma área acima</strong>
          <p id="resultado-desc" style="font-size: 0.85rem; color: var(--text-muted); margin-top: 6px;">
            Clique nos módulos do fluxograma para ver detalhes de atuação e métricas estimadas.
          </p>
        </div>
      </div>
    </section>

    <!-- Painel Lateral -->
    <aside class="sidebar">
      <h2>Métricas Estimadas</h2>
      
      <div class="metric-box">
        <p style="font-size: 0.85rem; color: var(--text-muted);">Redução de CO₂ / Ano</p>
        <div class="metric-value" id="metric-co2">0 Ton</div>
      </div>

      <div class="metric-box">
        <p style="font-size: 0.85rem; color: var(--text-muted);">Área Preservada</p>
        <div class="metric-value" id="metric-area">0 Hectares</div>
      </div>

      <div class="metric-box">
        <p style="font-size: 0.85rem; color: var(--text-muted);">Eficiência Energética</p>
        <div class="metric-value" id="metric-eficiencia">+0%</div>
      </div>

      <button class="btn-simular" onclick="executarSimulacao()">Executar Simulação Geral</button>
    </aside>
  </main>

  <footer>
    <p>Aplicação Web em ficheiro único • HTML5, CSS3 e JavaScript</p>
  </footer>

  <script>
    const dadosNos = {
      root: {
        titulo: "Central de Dados Ambientais",
        desc: "A recolha contínua via sensores e satélites alimenta modelos preditivos para tomada de decisão em tempo real.",
        co2: "120.000 Ton",
        area: "50.000 Hectares",
        eficiencia: "+15%"
      },
      florestas: {
        titulo: "Monitorização e Detecção de Incêndios",
        desc: "Algoritmos de visão computacional identificam fumo e desmatamento ilegal em minutos, enviando alertas automáticos.",
        co2: "450.000 Ton",
        area: "180.000 Hectares",
        eficiencia: "+40%"
      },
      energia: {
        titulo: "Otimização de Redes Renováveis",
        desc: "Previsão de produção eólica e solar ajusta o consumo e evita o desperdício de energia limpa.",
        co2: "800.000 Ton",
        area: "12.000 Hectares",
        eficiencia: "+65%"
      },
      oceanos: {
        titulo: "Mapeamento de Plástico nos Oceanos",
        desc: "Drones e satélites orientam embarcações para recolher manchas de resíduos nos pontos mais críticos.",
        co2: "90.000 Ton",
        area: "300.000 Hectares",
        eficiencia: "+30%"
      }
    };

    function selecionarNo(id) {
      document.querySelectorAll('.node').forEach(el => el.classList.remove('active'));
      const elSelecionado = document.getElementById(`node-${id}`) || event.currentTarget;
      elSelecionado.classList.add('active');

      const info = dadosNos[id];
      document.getElementById('resultado-titulo').innerText = info.titulo;
      document.getElementById('resultado-desc').innerText = info.desc;
      
      document.getElementById('metric-co2').innerText = info.co2;
      document.getElementById('metric-area').innerText = info.area;
      document.getElementById('metric-eficiencia').innerText = info.eficiencia;
    }

    function executarSimulacao() {
      let contador = 0;
      const intervalo = setInterval(() => {
        contador += 5;
        document.getElementById('metric-co2').innerText = `${contador * 15000} Ton`;
        document.getElementById('metric-area').innerText = `${contador * 8000} Hectares`;
        document.getElementById('metric-eficiencia').innerText = `+${Math.min(contador, 85)}%`;

        if (contador >= 85) {
          clearInterval(intervalo);
          document.getElementById('resultado-titulo').innerText = "Simulação Concluída!";
          document.getElementById('resultado-desc').innerText = "Impacto total projetado ao integrar todos os módulos de IA ambiental.";
        }
      }, 50);
    }
  </script>
</body>
</html>
