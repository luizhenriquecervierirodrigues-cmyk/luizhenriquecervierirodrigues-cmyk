<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Animação de Tinta CMYK</title>
    <style>
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #121212; /* Fundo escuro */
        }
        canvas {
            display: block;
        }
    </style>
</head>
<body>
    <canvas id="paintCanvas"></canvas>
    <script>
        const canvas = document.getElementById('paintCanvas');
        const ctx = canvas.getContext('2d');
        let particles = [];
        let numParticles = 40; // Número de gotas iniciais

        // Paleta de cores CMYK para a tinta
        const cmykColors = [
            'rgba(0, 255, 255, 0.5)',  // Ciano
            'rgba(255, 0, 255, 0.5)',  // Magenta
            'rgba(255, 255, 0, 0.5)',  // Amarelo
            'rgba(0, 0, 0, 0.3)'       // Preto (menos opaco para parecer mais suave)
        ];

        function resize() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }

        window.addEventListener('resize', resize);
        resize();

        class Particle {
            constructor(x, y, color) {
                this.x = x;
                this.y = y;
                this.color = color;
                this.vx = Math.random() * 6 - 3; // Velocidade horizontal aleatória
                this.vy = Math.random() * 10 + 2; // Velocidade vertical (caindo)
                this.radius = Math.random() * 20 + 10; // Tamanho inicial da gota
                this.life = Math.random() * 80 + 20; // Vida útil da gota
                this.gravity = 0.3; // Efeito da gravidade
                this.friction = 0.99; // Atrito para desacelerar
            }

            update() {
                this.vy += this.gravity;
                this.x += this.vx;
                this.y += this.vy;
                this.vx *= this.friction; // Desacelera horizontalmente
                this.radius *= 0.98; // Gota diminui de tamanho à medida que se espalha
                this.life--;
            }

            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();
            }
        }

        function createInkDrop() {
            for (let i = 0; i < 5; i++) { // Cria um pequeno "respingo" com 5 partículas
                const x = Math.random() * canvas.width;
                const y = -this.radius; // Começa acima da tela
                const color = cmykColors[Math.floor(Math.random() * cmykColors.length)];
                particles.push(new Particle(x, y, color));
            }
        }

        function animate() {
            // Cria um fundo semitransparente para criar o efeito de rastro
            ctx.fillStyle = 'rgba(18, 18, 18, 0.05)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            if (Math.random() < 0.2) { // Cria uma nova gota a cada poucos quadros
                createInkDrop();
            }

            particles = particles.filter(particle => {
                particle.update();
                particle.draw();
                return particle.life > 0 && particle.radius > 1; // Mantém a partícula apenas se tiver vida e tamanho
            });

            requestAnimationFrame(animate);
        }

        animate();
    </script>
</body>
</html>
