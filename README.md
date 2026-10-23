<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rodrigo Silvestre - Player Profile</title>
    <!-- Importando fontes para o visual gamificado/código -->
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;700&family=Press+Start+2P&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --bg-color: #0f172a;
            --panel-bg: #1e293b;
            --primary: #38bdf8;
            --success: #4ade80;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --html-color: #e34c26;
            --css-color: #264de4;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            font-family: 'Fira Code', monospace;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .game-container {
            background-color: var(--panel-bg);
            border: 2px solid var(--primary);
            border-radius: 15px;
            width: 100%;
            max-width: 700px;
            padding: 30px;
            box-shadow: 0 0 20px rgba(56, 189, 248, 0.2);
        }

        /* --- Player Header --- */
        .player-header {
            display: flex;
            align-items: center;
            gap: 20px;
            margin-bottom: 30px;
            flex-wrap: wrap;
            text-align: left;
        }

        .avatar {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            object-fit: cover;
            border: 4px solid var(--primary);
            box-shadow: 0 0 15px var(--primary);
            transition: transform 0.3s;
        }

        .avatar:hover {
            transform: scale(1.05);
        }

        .player-info h1 {
            font-family: 'Press Start 2P', cursive;
            font-size: 1.2rem;
            color: var(--primary);
            margin-bottom: 10px;
        }

        .player-info p {
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        /* --- Nível e XP (Gamificação) --- */
        .level-system {
            background: rgba(0,0,0,0.3);
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 30px;
        }

        .level-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-weight: bold;
        }

        .xp-bar-container {
            width: 100%;
            height: 20px;
            background-color: #334155;
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }

        .xp-bar {
            height: 100%;
            width: 30%; /* XP INICIAL */
            background: linear-gradient(90deg, #3b82f6, #38bdf8);
            transition: width 0.3s ease;
        }

        .btn-farm {
            margin-top: 15px;
            background-color: var(--success);
            color: #000;
            border: none;
            padding: 10px 20px;
            font-family: 'Fira Code', monospace;
            font-weight: bold;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            transition: background 0.2s, transform 0.1s;
        }

        .btn-farm:active {
            transform: scale(0.98);
        }

        /* --- Árvore de Habilidades --- */
        .skills-section {
            margin-bottom: 30px;
        }

        .skills-section h2 {
            font-size: 1.2rem;
            margin-bottom: 15px;
            border-bottom: 2px dashed var(--text-muted);
            padding-bottom: 5px;
        }

        .skill {
            margin-bottom: 15px;
        }

        .skill-name {
            display: flex;
            justify-content: space-between;
            margin-bottom: 5px;
        }

        .skill-bar-bg {
            width: 100%;
            height: 12px;
            background-color: #334155;
            border-radius: 6px;
        }

        .skill-bar-fill {
            height: 100%;
            border-radius: 6px;
        }

        .html-skill { background-color: var(--html-color); width: 85%; }
        .css-skill { background-color: var(--css-color); width: 75%; }

        .skill-desc {
            font-size: 0.8rem;
            color: var(--text-muted);
            margin-top: 4px;
        }

        /* --- README Terminal --- */
        .readme-terminal {
            background-color: #000;
            border: 1px solid #334155;
            border-radius: 8px;
            padding: 15px;
            position: relative;
        }

        .terminal-header {
            background-color: #334155;
            margin: -15px -15px 15px -15px;
            padding: 8px 15px;
            border-radius: 8px 8px 0 0;
            display: flex;
            gap: 8px;
        }

        .dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
        }
        .dot.red { background-color: #ff5f56; }
        .dot.yellow { background-color: #ffbd2e; }
        .dot.green { background-color: #27c93f; }

        .readme-content {
            color: #a5d6ff; /* Cor inspirada no markdown do github dark */
            font-size: 0.9rem;
            line-height: 1.6;
        }
        
        .readme-content h3 {
            color: #fff;
            margin-bottom: 10px;
        }
        
        .readme-content a {
            color: var(--primary);
            text-decoration: none;
        }
    </style>
</head>
<body>

    <div class="game-container">
        
        <!-- CABEÇALHO DO JOGADOR -->
        <header class="player-header">
            <!-- Substitua 'foto-curriculo.png' pela sua foto real -->
            <img src="foto-curriculo.png" alt="Foto de Rodrigo" class="avatar">
            <div class="player-info">
                <h1>Rodrigo Silvestre</h1>
                <p>Classe: Dev Full-Stack em Treinamento</p>
                <p>Background: Publicidade e Propaganda</p>
            </div>
        </header>

        <!-- SISTEMA DE GAMIFICAÇÃO -->
        <section class="level-system">
            <div class="level-header">
                <span id="player-level">Nível 5 - Analista Júnior</span>
                <span id="xp-text">300 / 1000 XP</span>
            </div>
            <div class="xp-bar-container">
                <div class="xp-bar" id="xp-bar"></div>
            </div>
            <button class="btn-farm" onclick="gainXP()">[ + ] Estudar Código (Ganhar XP)</button>
        </section>

        <!-- ÁRVORE DE HABILIDADES -->
        <section class="skills-section">
            <h2>&gt; Minhas Linguagens / Skills</h2>
            
            <div class="skill">
                <div class="skill-name">
                    <span>HTML5</span>
                    <span>85%</span>
                </div>
                <div class="skill-bar-bg">
                    <div class="skill-bar-fill html-skill"></div>
                </div>
                <p class="skill-desc">Construção de estrutura semântica, SEO básico e acessibilidade.</p>
            </div>

            <div class="skill">
                <div class="skill-name">
                    <span>CSS3</span>
                    <span>75%</span>
                </div>
                <div class="skill-bar-bg">
                    <div class="skill-bar-fill css-skill"></div>
                </div>
                <p class="skill-desc">Estilização, Flexbox, Grid Layout e design responsivo.</p>
            </div>
        </section>

        <!-- README SIMULADO DO GITHUB -->
        <section class="readme-terminal">
            <div class="terminal-header">
                <div class="dot red"></div>
                <div class="dot yellow"></div>
                <div class="dot green"></div>
            </div>
            <div class="readme-content">
                <h3># Olá, eu sou o Rodrigo! 👋</h3>
                <p>> Graduado em Publicidade e Propaganda, agora focado em transacionar e construir sistemas escaláveis e interfaces incríveis.</p>
                <br>
                <p><strong>🎯 Objetivo Atual:</strong> Cursando Tecnologia em Análise e Desenvolvimento de Sistemas (ADS).</p>
                <p><strong>🌱 Estudando:</strong> HTML, CSS e Lógica de Programação.</p>
                <p><strong>💡 Diferencial:</strong> Trago o olhar da Publicidade para entender o usuário, focando na união perfeita entre código, design e experiência.</p>
                <br>
                <p><i>"Convertendo café em linhas de código criativas."</i></p>
            </div>
        </section>

    </div>

    <!-- SCRIPT DA GAMIFICAÇÃO -->
    <script>
        let currentXP = 300;
        let maxXP = 1000;
        let currentLevel = 5;

        function gainXP() {
            // Ganha entre 50 e 120 de XP por clique
            const xpGained = Math.floor(Math.random() * 70) + 50; 
            currentXP += xpGained;

            if (currentXP >= maxXP) {
                // Level Up!
                currentLevel++;
                currentXP = currentXP - maxXP;
                maxXP = Math.floor(maxXP * 1.2); // Próximo nível precisa de mais XP
                alert(`🎉 LEVEL UP! Parabéns, você avançou para o Nível ${currentLevel}!`);
            }

            updateUI();
        }

        function updateUI() {
            const xpBar = document.getElementById('xp-bar');
            const xpText = document.getElementById('xp-text');
            const levelText = document.getElementById('player-level');

            // Calcula porcentagem e atualiza a barra
            const percentage = (currentXP / maxXP) * 100;
            xpBar.style.width = percentage + '%';

            // Atualiza os textos
            xpText.innerText = `${currentXP} / ${maxXP} XP`;
            levelText.innerText = `Nível ${currentLevel} - Analista Júnior`;
        }
    </script>
</body>
</html>
