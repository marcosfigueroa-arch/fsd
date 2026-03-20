<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8" />
<title>Mini Farming Simulator 19 - 2D</title>
<style>
  body {
    margin: 0;
    height: 100vh;
    overflow: hidden;
    background: #4a7043;
    font-family: Arial, sans-serif;
  }
  canvas {
    display: block;
  }
  #ui {
    position: absolute;
    top: 10px;
    left: 10px;
    color: white;
    background: rgba(0,0,0,0.5);
    padding: 10px 15px;
    border-radius: 8px;
    pointer-events: none;
  }
  #instructions {
    position: absolute;
    bottom: 15px;
    left: 50%;
    transform: translateX(-50%);
    color: #fff;
    background: rgba(0,0,0,0.6);
    padding: 10px 20px;
    border-radius: 10px;
    font-size: 0.9rem;
  }
</style>
</head>
<body>

<div id="ui">Grama colhida: <span id="score">0</span> l</div>
<div id="instructions">
  WASD / Setas = mover • ESPAÇO = subir/baixar tubo da forrageira
</div>

<canvas id="c"></canvas>

<script>
// ========================
//   MINI FARMING SIM 2D
// ========================

const canvas = document.getElementById('c');
const ctx = canvas.getContext('2d');
const scoreEl = document.getElementById('score');

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

window.addEventListener('resize', () => {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
});

// -----------------
//   INPUT
// -----------------
const keys = {};
window.addEventListener('keydown', e => keys[e.key.toLowerCase()] = true);
window.addEventListener('keyup',   e => keys[e.key.toLowerCase()] = false);

// -----------------
//   GAME STATE
// -----------------
let score = 0;
let time = 0;

const player = {
  x: canvas.width/2,
  y: canvas.height/2,
  angle: -Math.PI/2,     // olhando pra cima
  speed: 0,
  maxSpeed: 2.8,
  accel: 0.08,
  brake: 0.15,
  turnSpeed: 0.04,
  trailerAngle: -Math.PI/2,
  tubeUp: false
};

const trailer = {
  length: 110,
  width: 55
};

const grass = [];
for(let i = 0; i < 180; i++){
  grass.push({
    x: Math.random()*canvas.width*1.4 - canvas.width*0.2,
    y: Math.random()*canvas.height*1.4 - canvas.height*0.2,
    size: 18 + Math.random()*22
  });
}

// -----------------
//   UPDATE
// -----------------
function update() {
  time += 0.016;

  // Aceleração / Freio
  if (keys['w'] || keys['arrowup']) {
    player.speed = Math.min(player.speed + player.accel, player.maxSpeed);
  } else if (keys['s'] || keys['arrowdown']) {
    player.speed = Math.max(player.speed - player.accel*1.6, -player.maxSpeed*0.6);
  } else {
    // atrito
    player.speed *= 0.96;
  }

  // Curva
  const turn = (keys['a'] || keys['arrowleft'] ? 1 : 0) - (keys['d'] || keys['arrowright'] ? 1 : 0);
  player.angle += turn * player.turnSpeed * (Math.abs(player.speed)/player.maxSpeed) * 1.1;

  // Movimento
  player.x += Math.cos(player.angle) * player.speed;
  player.y += Math.sin(player.angle) * player.speed;

  // Trailer segue com atraso suave (estilo articulado)
  const targetAngle = Math.atan2(player.y - (player.y - Math.sin(player.angle)*trailer.length*0.8),
                                 player.x - (player.x - Math.cos(player.angle)*trailer.length*0.8));
  player.trailerAngle += (targetAngle - player.trailerAngle) * 0.12;

  // Tubo sobe/desce
  if (keys[' ']) {
    player.tubeUp = !player.tubeUp;
    keys[' '] = false; // evita ficar alternando rápido
  }

  // Colheita simples
  for (let i = grass.length-1; i >= 0; i--) {
    const g = grass[i];
    const dist = Math.hypot(g.x - player.x, g.y - player.y);
    if (dist < 75 && Math.abs(player.speed) > 0.4) {
      grass.splice(i,1);
      score += 120 + Math.floor(Math.random()*180);
      scoreEl.textContent = score.toLocaleString();
    }
  }

  // Limites do mapa (volta suave)
  if (player.x < -200) player.x = canvas.width + 200;
  if (player.x > canvas.width + 200) player.x = -200;
  if (player.y < -200) player.y = canvas.height + 200;
  if (player.y > canvas.height + 200) player.y = -200;
}

// -----------------
//   RENDER
// -----------------
function draw() {
  ctx.fillStyle = "#3a5c33";
  ctx.fillRect(0,0,canvas.width,canvas.height);

  // Grade de terra arada (efeito campo)
  ctx.strokeStyle = "rgba(90,70,40,0.25)";
  ctx.lineWidth = 2;
  for (let x = -200; x < canvas.width+200; x += 80) {
    ctx.beginPath();
    ctx.moveTo(x, -200);
    ctx.lineTo(x, canvas.height+200);
    ctx.stroke();
  }
  for (let y = -200; y < canvas.height+200; y += 80) {
    ctx.beginPath();
    ctx.moveTo(-200, y);
    ctx.lineTo(canvas.width+200, y);
    ctx.stroke();
  }

  // Grama restante
  ctx.fillStyle = "#6ab04c";
  grass.forEach(g => {
    ctx.beginPath();
    ctx.arc(g.x, g.y, g.size, 0, Math.PI*2);
    ctx.fill();
  });

  ctx.save();
  ctx.translate(player.x, player.y);
  ctx.rotate(player.angle);

  // Trailer (forrageira verde)
  ctx.save();
  ctx.translate(-trailer.length*0.8, 0);
  ctx.rotate(player.trailerAngle - player.angle);

  // Corpo principal da forrageira
  ctx.fillStyle = "#2e7d32"; // verde john deere like
  ctx.fillRect(-trailer.length/2 -10, -trailer.width/2, trailer.length + 40, trailer.width);

  // Cabeçote frontal (amarelo)
  ctx.fillStyle = "#fbc02d";
  ctx.fillRect(-trailer.length/2 - 60, -trailer.width/2 - 8, 80, trailer.width + 16);

  // Rodas grandes da forrageira
  ctx.fillStyle = "#212121";
  ctx.beginPath(); ctx.arc(-trailer.length*0.3, -trailer.width*0.45, 24,0,Math.PI*2); ctx.fill();
  ctx.beginPath(); ctx.arc(-trailer.length*0.3,  trailer.width*0.45, 24,0,Math.PI*2); ctx.fill();

  // Tubo alto (o mais característico)
  ctx.fillStyle = "#212121";
  ctx.fillRect(-trailer.length*0.1, -trailer.width*0.5 - 10, 140, 22);

  ctx.fillStyle = "#455a64";
  let tubeH = player.tubeUp ? -180 : -60;
  ctx.fillRect(-trailer.length*0.1 + 130, tubeH, 38, 180 + (player.tubeUp?140:0));

  ctx.restore();

  // Trator vermelho (frente)
  ctx.fillStyle = "#c62828"; // vermelho forte
  ctx.fillRect(-30, -38, 100, 76);

  // Cabine
  ctx.fillStyle = "#37474f";
  ctx.fillRect(20, -28, 50, 56);

  // Rodas do trator
  ctx.fillStyle = "#212121";
  ctx.beginPath(); ctx.arc(-10, -32, 32,0,Math.PI*2); ctx.fill();
  ctx.beginPath(); ctx.arc(-10,  32, 32,0,Math.PI*2); ctx.fill();
  ctx.beginPath(); ctx.arc(60, -25, 24,0,Math.PI*2); ctx.fill();
  ctx.beginPath(); ctx.arc(60,  25, 24,0,Math.PI*2); ctx.fill();

  // Faróis
  ctx.fillStyle = "#fff176";
  ctx.beginPath(); ctx.arc(85, -18, 8,0,Math.PI*2); ctx.fill();
  ctx.beginPath(); ctx.arc(85,  18, 8,0,Math.PI*2); ctx.fill();

  ctx.restore();

  // Poeira / rastros (simples)
  if (Math.abs(player.speed) > 0.8) {
    ctx.fillStyle = `rgba(140,110,70,${0.4 + Math.random()*0.3})`;
    ctx.beginPath();
    ctx.arc(player.x - Math.cos(player.angle)*80 + Math.sin(player.angle)*30, 
            player.y - Math.sin(player.angle)*80 - Math.cos(player.angle)*30, 22,0,Math.PI*2);
    ctx.fill();
  }
}

function loop() {
  update();
  draw();
  requestAnimationFrame(loop);
}

loop();

</script>
</body>
</html>