
let xBolinha = 275;
let yBolinha = 200;
let diametro = 17;
let raio = diametro /2;

let velocidadeXBolinha = 5;
let velocidadeYBolinha = 5;
let velocidadeRaquete2;


let meusPontos = 0;
let pontosOponente = 0;

let raquetada;
let ponto;
let trilha;

let xRaquete1 = 5
let yRaquete1 = 150
let xRaquete2 = 535
let yRaquete2 = 150
let raqueteWidth = 10
let raqueteHeight = 100

function preLoad(){
  trilha = loadSound("trilha.mp3");
  ponto = loadSound("ponto.mp3");
  raquetada = loadSound("raquetada.mp3");
  
}

function setup() {
  createCanvas(550, 400);
  loop("trilha.mp3");
}

function draw() {
  background(0);
  mostraBolinha();
  movimentaBolinha();
  verificaBorda ();
  mostraRaquete ();
  movimentoRaquete1 ();
  movimentoRaquete2 ();
  verificaColisaoRaquete();
  incluiPlacar();
  marcaPonto();
}

function mostraBolinha (){circle(xBolinha,yBolinha,diametro);}

function movimentaBolinha (){
  xBolinha += velocidadeXBolinha
  yBolinha += velocidadeYBolinha}

function verificaBorda (){  
  if (xBolinha + raio > width ||
     xBolinha - raio < 0){
    velocidadeXBolinha *= -1;
  }
   if (yBolinha + raio > height ||
     yBolinha - raio < 0){
     velocidadeYBolinha *= -1;
   }
}
     
function mostraRaquete (){rect (xRaquete1, yRaquete1, raqueteWidth, raqueteHeight)
  rect (xRaquete2, yRaquete2, raqueteWidth, raqueteHeight)}

function movimentoRaquete1(){
if (keyIsDown (UP_ARROW))
  yRaquete1 -= 10

if (keyIsDown (DOWN_ARROW))
  yRaquete1 += 10
}
  function verificaColisaoRaquete(){ 
  if (xBolinha - raio < xRaquete1 + raqueteWidth && yBolinha - raio < yRaquete1 + raqueteHeight && yBolinha + raio > yRaquete1){
    velocidadeXBolinha *= -1
    
  }
  }

function movimentoRaquete2 (){
velocidadeRaquete2 = yBolinha - yRaquete2 - raqueteHeight/ 2;
  yRaquete2 += velocidadeRaquete2
  }

function incluiPlacar(){
  stroke(255)
  textAlign(CENTER)
  textSize(16);
  fill(color (255,140,0));
  rect (140,10,40,20);
  fill(255);
text(meusPontos, 160,26);
  fill(color (255,140,0));
  rect (410, 10, 40, 20);
  fill(255);
  text(pontosOponente, 430, 26);
  
}

function marcaPonto (){
if (xBolinha + raio > 550){
meusPontos += 1
}
  if (xBolinha - raio < 0){
  pontosOponente += 1
  }
}
