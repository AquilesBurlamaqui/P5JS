# Tutorial P5Js

## Passo 1: Criando um arquivo html com a biblioteca P5js - https://p5js.org/

Para criar seu jogo usando o P5JS você precisará de uma página HTML com a tag <script src=""> apontando para o código da biblioteca p5js. Copie o código abaixo e salve como jogo.html. Depois abra em seu navegador preferido. 

#### jogo.html
``` html
<html>
<head>
  <meta charset="UTF-8">
  <script language="javascript" type="text/javascript" src="https://github.com/processing/p5.js/releases/download/0.5.16/p5.js"></script>
  <script>
     //seu código p5js vai aqui:
     function setup() {
      	createCanvas(640, 480);
      	background(0,0,0);
     }

     function draw() {
        ellipse(50, 50, 80, 80);
     }
  </script>
</head>
<body>
    
</body>
</html>
```

No caso do código acima, temos a 2 funções principais do p5js, a function setup() e function draw().  
A setup() só é executada uma única vez, e serve para configurar parâmetros, variáveis, etc.
A draw() é utilizada para redesenhar a tela diversas vezes, em um loop, como se fosse um while(true) ou laço infinito.  Permitindo com isso a criação de animacoes. 

createCanvas uma área de desenho de 640 pixels de largura por 480 pixels de altura
```javascript
createCanvas(640, 480);
```

background pinta a tela de fundo(background) de preto. Essa funcao recebe as cores no formato R, G, B(Red, Green Blue). Como todas as cores estão com zero a cor é preta. Para conseguir um background azul bastaria colocar background(0,0,255); 255 no B, blue(azul).
```javascript
background(0,0,0);
```
uma elipse é desenhada na tela. 
Para isso, temos que informar as coordenadas e o tamanho da elipse usando *ellipse([coordenada x],[coordenada y], [largura], [altura])*. 
```javascript
 ellipse(50, 50, 80, 80);
```

### Passo 1.1 (Alternativo)
A opção acima depende da internet para funcionar, pois o código do p5js esta apontando para um link na web. Alternativamente, você pode optar por baixar o código do p5js (p5.js) em seu diretório local e apontar para ele, deixando seu código autocontido. Veja o exemplo a seguir e note que aproveitamos e colocamos o script do nosso jogo tambem em um arquivo separado (scriptjogo.js).

#### jogo.html
``` html
<html>
<head>
  <meta charset="UTF-8">
  <script language="javascript" type="text/javascript" src="js/p5.js"></script>
  <script language="javascript" type="text/javascript" src="scriptjogo.js"></script>

</head>

<body>
</body>
</html>
```

#### scriptjogo.js
``` javascript
function setup() {
	createCanvas(640, 480);
	background(0);
 }

 function draw() {
        ellipse(50, 50, 80, 80);
 }
```



O resultado da execução do arquivo index.html será: 

![Elipse](imagens/p1.png)

Para mais informações veja: 

* https://p5js.org/reference/#/p5/ellipse 

Um exemplo de código funcionando com processing web (p5.js) pode ser baixado em: https://github.com/AquilesBurlamaqui/P5JS/raw/master/jogoP5js.zip

## Passo 2: Desenhando formas geométricas e usando o editor do p5js 

O processing tem diversas funções para desenho de formas, tais como `ellipse()`, `rect()`, `line()`, `point()`, `quad()`, `triangle()`... Todas elas precisam de informações como posição e tamanho, que são colocadas dentro dos parênteses.

Já que você aprendeu como criar um arquivo html e colocar o script do p5js para funcionar nesse arquivo, vamos agora tentar fazer o mesmo utilizando o editor do próprio sie do p5js:  https://editor.p5js.org/
Ele é uma maneira mais prática de testar e ate mesmo, caso vc crie uma conta na plataforma deles, de criar e publicar seu jogo.
Abram o link https://editor.p5js.org/ e coloquem o seguinte código:

``` javascript
function setup() {
	createCanvas(640, 480);
	background(0,0,0);
}

function draw() {
  //cabeca
  //preenchimento branco
  fill(255, 255, 255);
  //cor da linha AZUL (R(0), G(0), B(255))
  stroke(0, 0, 255);
  //desenha retangulo
  rect(100, 50, 400, 350);
  
  //olhos
  noFill();
  stroke(0, 0, 255);
  ellipse(200, 100, 120, 60);
  ellipse(400, 100, 120, 60);

  //nariz
  noStroke();
  fill(255, 0, 0);
  rect(260, 200, 80, 80);
  
  //boca
  stroke(60, 150, 60);
  strokeWeight(5);
  line(200, 300, 400, 350);
}
```
Resultado da execução:

![Elipse](imagens/p2.png)

Como vimos, função createCanvas() define o tamanho da tela e o background() define sua cor de fundo. Já as funções fill() e stroke(), definem as cores de preenchimento e de contorno, respectivamente. Uma vez utilizadas essas funções, seus efeitos valerão para todas as formas declaradas abaixo. noFill() e noStroke(), retiram o preenchimento e o contorno, respectivamente, e strokeWeight() define uma espessura para o contorno da forma.
  
 Veja:
 
 * https://p5js.org/reference/#/p5/rect
 * https://p5js.org/reference/#/p5/line
 * https://p5js.org/reference/#/p5/fill
 * https://p5js.org/reference/#/p5/noFill
 * https://p5js.org/reference/#/p5/stroke
 * https://p5js.org/reference/#/p5/noStroke
 * https://p5js.org/reference/#/p5/createCanvas
  
  
## Passo 3: Utlizando a posição do MOUSE - acesso as variáveis globais mouseY e mouseX,

Primeiro teremos que saber o que são as funções setup() e draw(), que viemos utilizando aqui. Elas são usadas basicamente para organizar o fluxo do código. O setup(), é executado apenas uma vez, no começo, para declarações iniciais. Já o draw(), ficará se repetindo no decorrer da execução, nele poderemos fazer algo mudar seu valor ao longo do tempo. Um exemplo é a posição da ellipse, que pode ser alterada de acordo com a posiço do mouse!

Veja:

* https://p5js.org/reference/#/p5/setup
* https://p5js.org/reference/#/p5/draw

Delete o script anterior e digite o seguinte: 

``` javascript
function setup() {
  createCanvas(640, 480);
  noFill();
}

function draw() {
  ellipse(mouseX, mouseY, 80, 80);
}
```
Resultado da execução:

![Elipse](imagens/p3.png)

Os parâmetros mouseY e mouseX, funcionam como variáveis que armazenam os valores da posição do mouse.

Veja:

* https://p5js.org/reference/#/p5/mouseX
* https://p5js.org/reference/#/p5/mouseY

## Passo 4: Detectando se o mouse foi pressionado

Agora vamos implementar um pouco esse código.

``` javascript
function setup() {
  createCanvas(640, 480);
  noFill();
}

function draw() {
  if (mouseIsPressed){
    ellipse(mouseX, mouseY, 100, 100);
  }
}

```
![Elipse](imagens/p4.png)

A variável mouseIsPressed é uma boleana, nela é armazenado true para o caso de o botão do mouse estar sendo pressionado e false para o caso do botão estar solto.

Veja: 

* https://p5js.org/reference/#/p5/mouseIsPressed

## Passo 5: Utilizando a função random para gerar números aleatórios

A função random(min, max) também pode ser muito útil para diversas aplicações.
	
``` javascript
function setup() {
  createCanvas(640, 480);
  noFill();
}

function draw() {
  if (mouseIsPressed){
    ellipse(mouseX, mouseY, random(100, 200), random(100, 200));
  }
}

```

![Elipse](imagens/p5.png)

Veja:

* https://p5js.org/reference/#/p5/random


## Passo 6: Criando novas varáveis globais - pré-tiro 

Também podemos criar nossas próprias variáveis.

``` javascript
var posX, posY;

function setup() {
  createCanvas(640, 480);
  posX = 0;
  posY = 200;
}

function draw() {
  background(0);
  if (posX < 640){
	posX = posX + 15;
  }else{
	posX = 0;
  }
  ellipse(posX, posY, 50, 50);
}
```
![Elipse](imagens/p6.png)

Aqui, criamos as variáveis antes das funções, para que elas possam ser usadas em todos os lugares do código. No setup(), damos valores iniciais, visto que o setup só é executado uma única vez. No draw(), verificamos se a posição X do círculo está dentro do nosso canvas, se está verdadeiro, a variável da posição X é incrementada fazendo com que o círculo ande pela tela na horizontal, se ele sai do canvas, a posição X volta para zero (0) e o ciclo recomeça. O background está sendo repintado no draw() para evitar que o círculo deixe um rastro na tela; primeiro é pintado um fundo, depois o círculo é pintado em uma posição X, depois o fundo é pintado novamente e só então um novo círculo é pintado, em uma nova posição X. Experimente retirar a função background e veja o que acontece.

## Passo 7 : Controlando uma elipse com as setas do teclado 
```javascript
var x = 100;
var y = 100;

function setup() {
  createCanvas(512, 512);
}

function draw() {
  background(0);
  if (keyIsDown(LEFT_ARROW))
    x-=5;

  if (keyIsDown(RIGHT_ARROW))
    x+=5;

  if (keyIsDown(UP_ARROW))
    y-=5;

  if (keyIsDown(DOWN_ARROW))
    y+=5;
	
  ellipse(x, y, 50, 50);
}
```
Neste código, utilizamos entradas do teclado para alterar os valores das variáveis criadas. Isso é feito atravéz da função keyIsDown(), que retorna true sempre que uma tecla com o mesmo código que foi passado como parâmetro na função estiver sendo pressionada, e false caso contrário. Você poderá usar o número que representa a tecla ou o próprio nome reservado para ela como: BACKSPACE, DELETE, ENTER, RETURN, TAB, ESCAPE, SHIFT, CONTROL, OPTION, ALT, UP_ARROW, DOWN_ARROW, LEFT_ARROW, RIGHT_ARROW. Para saber o número que representa qualquer tecla, veja: http://keycode.info/. 

Veja: 

* https://p5js.org/reference/#/p5/keyIsDown.

## Passo 8 : Random + Mouse pressionado

Vejamos agora mais algumas aplicações da função random().
```javascript
var yo, xo;

function setup() {
  createCanvas(512, 512);
  yo = random(512); 
  xo = random(512);
}

function draw() {
  background(0);
  
  if(mouseIsPressed) {
		yo = random(512);
		xo = random(512);
  }
  
  rect(xo,yo,40,40);
}
```

Neste código, a função foi utilizada para definir uma posição aleatória para um retangulo, dentro do nosso canvas, sempre que o botão do mouse for pressionado. Observe que passamos apenas um valor como parâmetro, tal valor é interpretado como o valor máximo e o número escolhido estará na faixa [0, max]. Poderiamos também definir a posição do retangulo para fora do canvas, e faze-lo aparecer utilizando o sistema de movimentação que já vimos antes.

## Passo 9 : Random quando sair da tela
```javascript
var yo, xo;

function setup() {
   createCanvas(512, 512);
   yo = random(512); 
   xo = -random(512);
}

function draw() {
   background(0);
  
   xo += 10;
  
   if(xo > width) {
     yo = random(512);
     xo = -random(512); 
   }
  
   rect(xo,yo,40,40);
}
```
Note que após o retangulo sair da área do nosso canvas, devemos definir as posições novamente, para que ele volte a aparecer no começo da tela.

Veja:

* https://p5js.org/reference/#/p5/random

## Passo 10 : Variáveis de estado

Introduziremos agora o conceito de *variáveis de estado*. Utilizar variáveis de estado é muito útil para quando precisamos que algo aconteça no programa somente quando alguma outra ação estiver sendo realizada. Por exemplo, você só poderá fazer provas de C2 enquanto a *variável* "cursando C2" estiver ativada, uma vez que essa variável seja desligada você não poderá mais fazer provas de C2 a não ser que "cursando C2" seja ligada novamente ('-'). Para criar uma variável de estado utilizamos as variáveis boleanas, pois estas possuem dois estados, *true* e *false*, que são usados para representar *ligado* e *desligado*.

Vejamos um exemplo prático dessas variáveis de estado.

```javascript
var yo, xo;
var naTela = true;
function setup() {
  createCanvas(512, 512);
  yo = random(512); 
  xo = 15;
}

function draw() {
  background(0);
  
  if(naTela){
    xo += 15;
  }else{
    yo = random(512); 
    xo = 15;
    naTela = true;
  }
  
  if(xo > width) {
	naTela = false;
  }
  
  rect(xo,yo,40,40);
}
```

Aqui, a variável boleana naTela funciona como variável de estado, pois observe que enquanto o retângulo permanecer dentro da área do canvas, naTela é verdadeira e o retângulo anda para a direita, uma vez que este saia da tela, naTela vira falso e o retângulo volta para o começo da tela. Em resumo, podemos ler que o retângulo andará quando naTela for verdadeiro e voltará para o começo da tela quando naTela for falso. Vejamos outro exemplo.

## Passo 11 : Variável de estado para implementar algo como um pré-tiro
```javascript
var yo, xo;
var podeMudar = true;
function setup() {
  createCanvas(512, 512);
  yo = random(512); 
  xo = 15;
}

function draw() {
  background(0);
  
  if(!podeMudar){
     xo += 15;
  }
  
  if(xo > width){
	podeMudar = true;
  }
  
  if(mouseIsPressed && podeMudar) {
      yo = random(512); 
      xo = 15;
    podeMudar = false;
  }
  
  rect(xo,yo,40,40);
}
```

Aqui a variável de estado é podeMudar. O programa funciona da seguinte forma: quando o mouse é clicado, uma posição é definida para o retângulo que logo então começará a andar para a direita, uma vez em movimento, o clique do mouse não conseguirá mais mudar sua posição até que ele saia da área do canvas. Assim, quando o retângulo estiver fora de vista, podeMudar é verdadeira e a posição poderá ser alterada com um clique do mouse, mas uma vez em movimento, até que o retângulo saia de vista novamente, podeMudar será falsa e o clique do mouse não funcionará. 

## Passo 12 :Escrevendo textos na tela

Em alguns casos, precisaremos escrever algo na nossa tela, podemos fazer isso usando a função text(), desse modo:

```javascript
var posX, posY;
var contagem = 0;
function setup() {
  createCanvas(640, 480);
  posX = 0;
  posY = 200;
}

function draw() {
  background(0);
  
  textSize(14); // define o tamanho da fonte
  fill(255); 
  text("Ja passaram " + contagem + " bolas.", 250, 15); // escreve na tela, note que podemos imprimir o valor de variáveis.
  
  if (posX < 640){
	posX = posX + 15;
  }else{
	contagem++;
	posX = 0;
  }
  ellipse(posX, posY, 50, 50);
}
```

Saída: 

![Elipse](imagens/p7.png)

## Passo 13 :Calculando a distância entre dois pontos

Outra função bastante utilizada é a dist(x1, y1, x2, y2), que retorna a distancia entre duas posições informadas. Podemos utiliza-la de diversas formas, veremos um exemplo aqui.

``` javascript
var x1 = 10;
var y1 = 90;

function setup(){
	createCanvas(500, 420);
}

function draw() {
  background(200);
  fill(0);

  var x2 = mouseX;
  var y2 = mouseY;

  line(x1, y1, x2, y2);
  ellipse(x1, y1, 7, 7);
  ellipse(x2, y2, 7, 7);

  var d = int(dist(x1, y1, x2, y2));
  textSize(20);
  text("A distancia entre os pontos é " + d + " pixeis.", 80, 400);
}
```

Saída: 
![Elipse](imagens/p8.png)


## Passo 14 :Adicionando uma musica ao seu código

```  html

<html>
<head>
  <meta charset="UTF-8">
  <script language="javascript" type="text/javascript" src="https://github.com/processing/p5.js/releases/download/0.5.16/p5.js"></script>
  <script language="javascript" type="text/javascript" src="jogo.js"></script>
<embed name="musica" src="musica.mp3" loop="true" hidden="true" autostart="true"> //mudança



  <style> body {padding: 0; margin: 0;} </style>
</head>

<body>
</body>
</html>

	
```
Foi adicionado uma linha de código com:
```	
<embed name="musica" src="musica.mp3" loop="true" hidden="true" autostart="true">
```
Isso permite que importemos o arquivo "musica.mp3" do nosso diretório;

também podemos importar uma musica da web utilizando endereço URL da musica, por exemplo:
```
<html>
<head>
  <meta charset="UTF-8">
  <script language="javascript" type="text/javascript" src="https://github.com/processing/p5.js/releases/download/0.5.16/p5.js"></script>
  <script language="javascript" type="text/javascript" src="jogo.js"></script>
<embed name="musica" src="http://66.90.93.122/ost/dragon-ball-revenge-of-king-piccolo-2009/chgpgoboug/BGM%20001.mp3" loop="true" hidden="true" autostart="true"> //mudança



  <style> body {padding: 0; margin: 0;} </style>
</head>

<body>
</body>
</html>
```
## PAsso 15 - Menu utilizando setas

``` javascript
var x = 80;
var y = 100;

var tela = 0;
var opcao = 1;

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
  if(tela==0) 
    menu();
  if(tela==1)
    fase1();
  if(tela==2)
    instrucoes();
  if(tela==3)
    creditos();
}

function menu() {
  rect(x, y, 200, 45);
  
  textSize(32);
  text('ECT GAME', 120, 50);
  text('Jogar', 90, 130);
  text('Instruções', 90, 230);
  text('Créditos', 90, 330);
}

function fase1() {
  textSize(32);
  text('FASE 1',10, 50);
}

function instrucoes() {
  textSize(32);
  text('Instruções',10, 50);
}

function creditos() {
  textSize(32);
  text('Creditos',10, 50);
}

function keyPressed() {
  if (key === 'ArrowUp' && y>100) {
    y-=100;
    opcao--;
  } else if (key === 'ArrowDown' && y<300) {
   y+=100;
    opcao++;
  } else if (key === 'Enter') {
   tela=opcao;
  } else if (key === 'Escape') {
   tela=0;
  }
}
```
					   
## PAsso 16 - Menu utilizando o Mouse

``` javascript	
//tela
//  0  menu
//  1 jogar
//  2 creditos
var tela=0;

var score = 0;

var pX=0;
var pY=100;

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(220);
  
  if(tela==0) {
    textSize(25);
    textAlign(CENTER);
    text("MENU", 200,30);

    rect(135, 200, 125, 45, 10);
    text("JOGAR", 200,230);

    rect(130, 275, 140, 45, 10);
    text("CREDITOS", 200,305);
  }
  
  if(tela==1) {
    textSize(25);
    textAlign(CENTER);
    text("JOGAR", 200,30);
    ellipse(pX,pY, 40,40);
    pX=pX+5;
    if(pX>400) {
      pX=0;
    }
    //botao voltar
    textSize(16);
    rect(330, 10, 25, 25, 10);
    text("Voltar", 375,25);
    
    text("Score:"+score, 30,50);
  }
  
  if(tela==2) {
    textSize(25);
    textAlign(CENTER);
    text("CREDITOS", 200,30); 
  }
 
  textSize(12);
  text(mouseX+" "+mouseY, 30,30);
  text("tela "+tela, 30,40);
 
}

function mousePressed() {
  if(tela==0) {
    if(mouseX>135 && mouseX<260 && mouseY>200 && mouseY<245) {
      console.log("Clicou em Jogar!!!");
      tela=1;
    }else if(mouseX>130 && mouseX<270 && mouseY>275 && mouseY<320) {
      console.log("Clicou em Creditos!!!");
      tela=2;
    }
  }
  
  if(tela==1) {
     if(mouseX>330 && mouseX<355 && mouseY>10 && mouseY<35) {
        console.log("Clicou em voltar!!!");
        tela=0;
     }  
  }
}

function keyPressed() {
   if(keyCode==27) {
     tela=0;
   }
}
```							    
					   
					   
					   

Por enquanto, pode parecer que não fizemos algo muito interessante, mas essa é só uma base para que você possa criar coisas incríveis. Para isso, basta praticar os conceitos aqui mostrados e juntar-los ao que vocè aprender em suas pesquisas futuras. Um ótimo lugar para expandir seu conhecimento sobre esse assunto é o próprio site do Processing. Divirta-se!

					   
					   
					   
Saiba mais em: 
* https://p5js.org/
