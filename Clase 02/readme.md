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

