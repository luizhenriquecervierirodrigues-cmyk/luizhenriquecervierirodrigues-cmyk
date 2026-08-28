<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 220" width="100%">
  <defs>
    <!-- Gradiente animado em movimento (Roxo e Magenta) -->
    <linearGradient id="bgGrad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" stop-color="#1e0036">
        <animate attributeName="stop-color" values="#1e0036;#3c096c;#5a189a;#7b2cbf;#1e0036" dur="8s" repeatCount="indefinite" />
      </stop>
      <stop offset="50%" stop-color="#7209b7">
        <animate attributeName="stop-color" values="#7209b7;#b5179e;#ff007f;#7209b7" dur="6s" repeatCount="indefinite" />
      </stop>
      <stop offset="100%" stop-color="#f72585">
        <animate attributeName="stop-color" values="#f72585;#7209b7;#3a0ca3;#f72585" dur="8s" repeatCount="indefinite" />
      </stop>
    </linearGradient>

    <!-- Filtro de Brilho Neon para o Texto -->
    <filter id="neonGlow" x="-50%" y="-50%" width="200%" height="200%">
      <feGaussianBlur stdDeviation="3" result="blur1" />
      <feGaussianBlur stdDeviation="8" result="blur2" />
      <feGaussianBlur stdDeviation="16" result="blur3" />
      <feMerge>
        <feMergeNode in="blur3" />
        <feMergeNode in="blur2" />
        <feMergeNode in="blur1" />
        <feMergeNode in="SourceGraphic" />
      </feMerge>
    </filter>
  </defs>

  <style>
    .bg {
      fill: url(#bgGrad);
    }

    /* Bolhas de tinta em movimento */
    .cyan { fill: #00FFFF; opacity: 0.45; mix-blend-mode: screen; animation: moveCyan 7s infinite alternate ease-in-out; }
    .magenta { fill: #FF00FF; opacity: 0.55; mix-blend-mode: screen; animation: moveMagenta 9s infinite alternate ease-in-out; }
    .yellow { fill: #FFFF00; opacity: 0.4; mix-blend-mode: screen; animation: moveYellow 6s infinite alternate ease-in-out; }

    @keyframes moveCyan {
      0% { transform: translate(120px, 110px) scale(0.9); }
      100% { transform: translate(450px, 70px) scale(1.4); }
    }
    @keyframes moveMagenta {
      0% { transform: translate(650px, 130px) scale(1.3); }
      100% { transform: translate(300px, 100px) scale(0.8); }
    }
    @keyframes moveYellow {
      0% { transform: translate(380px, 60px) scale(0.7); }
      100% { transform: translate(520px, 150px) scale(1.3); }
    }

    /* Texto Pulsante e Brilhante */
    .pulse-text {
      font-family: 'Segoe UI', Ubuntu, 'Arial Black', sans-serif;
      font-weight: 900;
      fill: #FFFFFF;
      font-size: 38px;
      letter-spacing: 5px;
      transform-box: fill-box;
      transform-origin: center;
      filter: url(#neonGlow);
      animation: pulse 2.2s infinite ease-in-out;
    }

    @keyframes pulse {
      0% {
        transform: scale(0.95);
        opacity: 0.85;
      }
      50% {
        transform: scale(1.06);
        opacity: 1;
      }
      100% {
        transform: scale(0.95);
        opacity: 0.85;
      }
    }
  </style>

  <!-- Fundo com gradiente animado -->
  <rect class="bg" width="800" height="220" rx="16"/>

  <!-- Tintas em movimento -->
  <g>
    <circle class="cyan" r="75" />
    <circle class="magenta" r="80" />
    <circle class="yellow" r="70" />
  </g>

  <!-- Texto com brilho e pulso -->
  <text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" class="pulse-text">
    LUIZ CERVIERI
  </text>
</svg>
