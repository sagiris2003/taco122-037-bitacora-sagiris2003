# Clase 02 14/08/2025

se repasan los contenidos de la clase anterior
revisamos la bitácora de Gato, el profe comenta que está muy buena
en base a esto me doy cuenta que debo mejorar la mía

El computador funciona con código binario: el profe expli el "iceberg" de la programación de un computador
-> diferencia entre alto y bajo nivel: uno es una simplificación del anterior

## Processing
descargamos processing
Processing es un lenguaje de programación basado en java

El profe nos hace una introducción a processing, explicando conceptos para una programación básica
algunos apuntes que logré sacar:

Print es una función
Todas las funciones en Processing se describen así
  -> Print ("hola mundo");
  lo que genera esto: hola mundo

Variables
  -> son números o datos
  -> se crean definiendo el tipo de variable
    -> tipo de variable es un contenedor
  -> char no sirve para los números

Generación de imagen
  -> dibujamos una línea
  -> las variables se suelen crear antes del setup

## Encargo
introducir en Processing los textos que escogimos, con algunas figuras, con movimiento y basándose en el contructivismo ruso

## Códigos que usamos esta clase
durante la clase intenté seguir el ritmo mientras el profe explicaba Processing, hice algunos códigos, los cuales al principio se podían ejecutar, pero luego no. Aquí un ejemplo

int cantidad = 0;

background (200);

//si quiero que las lineas aparezcan delante
//debo crearlas despues de pintar el fondo

line (10,200,250,100);
line (30,10,300,500);

textSize(30);
fill (0); //relleno de negro
text("saludos", 150, 500);

void setup (){
  //aqui ocurren cosas
size (400,600);
}

void draw (){
  //y aqui ocurren otras cosas
}



No funcionaba así que le pregunté a chatgpt qué podría ser, me lo corrigió y me dio esta opción
"tu código está mezclando instrucciones que deberían ir dentro de setup() o draw() con otras que pusiste sueltas, y eso en Processing no va a funcionar como esperas. Luego me mandó la correción

int cantidad = 0;

void setup() {
  size(400, 600);
  background(200); // Pintamos el fondo una vez
}

void draw() {
  // Dibujamos las líneas
  line(10, 200, 250, 100);
  line(30, 10, 300, 500);

  // Texto
  textSize(30);
  fill(0); // Relleno negro
  text("saludos", 150, 500);
}

## próxima entrega
El profe nos mandó de tarea usar el texto que queremos trabajar, con los siguientes requerimientos:
- debemos basarnos en el constructivismo ruso
- debe tener movimiento

la verdad no soy una persona muy "computin" como se dice coloquialmente, por lo que en la clase no logré comprender todos los conceptos a aplicar en Processing, así que le pedí a chatgpt que hiciera un código. Luego de pedirle y corregir 10 veces, logré algo cercano a lo que quería. Lo pongo a continuación

// Afiche Constructivista Animado con Líneas Rojas y Nueva Línea Izquierda

PFont font;

// Variables triángulo giratorio (arriba izq.)
float angulo = 0;

// Variables círculo central
float posX;
boolean derecha = true;

// Variables texto
float textoX;
boolean proyectando = true;

void setup() {
  size(900, 600);
  font = createFont("Arial-Bold", 22);
  textFont(font);
  textAlign(LEFT, CENTER);
  
  posX = width/2;
  textoX = 120; // posición inicial desde el proyector
}

void draw() {
  background(120); // fondo gris oscuro
  
  // --- Triángulo girando (arriba izquierda, grande) ---
  pushMatrix();
  translate(120, 120);
  rotate(radians(angulo));
  fill(200, 0, 0);
  noStroke();
  triangle(-80, 80, 80, 80, 0, -120); // triángulo grande
  popMatrix();
  
  angulo += 0.5; // velocidad de rotación
  
  // --- Línea abajo derecha (roja) ---
  stroke(255, 0, 0); // roja
  strokeWeight(18); // más gruesa
  line(width-180, height, width, height-180);
  
  // --- Línea izquierda (nueva) ---
  stroke(0); // negra
  strokeWeight(14); // gruesa
  line(60, 0, 150, height/2); // diagonal desde parte izquierda superior
  
  // --- Cuadrado muy grueso, pegado a la esquina superior derecha ---
  stroke(0);
  strokeWeight(28); // muy grueso
  noFill();
  
  float tamCuadrado = 400; // tamaño del cuadrado
  rectMode(CORNER);
  rect(width - tamCuadrado, 0, tamCuadrado, tamCuadrado); // pegado a esquina superior derecha
  
  // --- Círculo central en movimiento ---
  noStroke();
  fill(0);
  ellipse(posX, height/2, 100, 100);
  
  if (derecha) {
    posX += 2;
    if (posX > width - 100) derecha = false;
  } else {
    posX -= 2;
    if (posX < 100) derecha = true;
  }
  
  // --- Proyector (abajo izquierda) ---
  fill(50);
  rect(50, height-120, 60, 60); // cuerpo
  triangle(110, height-120, 150, height-90, 110, height-60); // lente
  
  // --- Haz de luz proyectado ---
  noStroke();
  fill(255, 220, 150, 180); // luz amarillenta semitransparente
  beginShape();
  vertex(110, height-120);
  vertex(110, height-60);
  vertex(width, height-200);
  vertex(width, height);
  endShape(CLOSE);
  
  // --- Texto dentro del haz ---
  fill(0);
  text("PARA NOSOTROS EL CINE COMIENZA CON CADA", textoX, height-90);
  text("NUEVO ZUMBIDO DEL PROYECTOR", textoX, height-60);
  
  // Movimiento del texto (sale y vuelve a entrar)
  if (proyectando) {
    textoX += 2; // avanza hacia la derecha
    if (textoX > width - 400) {
      proyectando = false;
    }
  } else {
    textoX -= 2; // regresa al proyector
    if (textoX < 120) {
      proyectando = true;
    }
  }
}

Como me interesa aprender, le pedí a chatgpt que me fuera explicando paso por paso qué fue lo que hizo
Le hice un ajuste a esta parte

// Variables círculo central
float posX;
boolean derecha = true;

lo cambié por

// Variables círculo central
float posX;
boolean derecha = false;

esto lo hice para que el círculo fuera hacia la izquierda en vez de la derecha, así el peso visual no se carga a la derecha y el movimiento del círculo se contrasta con el de la frase.
