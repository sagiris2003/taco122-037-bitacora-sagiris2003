# Clase 03

Recuerdo de mi primera clase tomando apuntes en github y no en papel.

FORK (tenedor): te crea una copia de un repositorio ajeno, puedes estar sincronizado, estar adelantado o atrasado con respecto al repositorio principal. Si te atrasas puedes sincronizarlo.

## imagenes
Para subir imágenes debemos crear una carte aparte, la cual debe contener las imágenes que queremos. Luego debemos rutearla (en nuestro readme) con el siguiente código

```
![TEXTO ALTERNATIVO](./IMÁGENES/NOMBREDELARCHIVO.FORMATO)
```

![pantera rosa](./imágenes/Panterarosa.png)

## Códigos
para que los códigos se vean como códigos se deben poner tildes invertidas al inicio y al final.
```
CÓDIGO
```

## Arduino
Comenzamos a ver Arduino
- Ingresamos a Arduino.cc y le damos permiso para todo
- luego debemos descargar un driver para que la app se comunique con nuestro arduino que es copia (uno compatible). El driver se llama "Driver ch340"

¿Qué hace arduino?
- tiene inputs y outputs
- recibe información de sensores, los convierte en datos y tiene actuadores
    Tipos de actuadores: motores, luces, sonidos
  Digital In solo recibe órdenes binarias: 0 o 1, encendido o apagado, high o low

Estando dentro de Arduino el profe nos fue explicando cómo configurarlo.

Primero vemos cómo encender y apagar la luz.
se debe crear una variable para indicar dónde está el led

```
int ledPin = 13;
int tiempoOn = 200;
int tiempoOff = 100;
```
debemos saber si los pines que usaremos son inputs u outputs
el led que usa arduino está conectado a la pata 13, por lo que debemos decirle al arduino que esa pata sea output

```
void setup ()
{
pinMode(ledPin,OUTPUT);
}

void loop ()
{
//debemos "escribir" en el led para encenderlo
//se usa la funcion
//digitalWrite(numeroDePin, estado0o1);
digitalWrite(ledPin,HIGH);
//con el delay paralizamos el codigo por un tiempo en milisegundos
delay(tiempoOn)
//apagamos el led
digitalWrite(ledPin,LOW);
delay(tiempoOff);
}
```

### uso de serial print
para que lo que hace nuestro arduino, tenga una visualización en el programa

```
int ledPin = 13;
int tiempoOn = 200;
int tiempoOff = 100;

void setup()
{
    pinMode(ledPin,OUTPUT);
    //9600 es el baud rate
    //o tasa de baudios
    Serial.begin(9600);
}

void loop()
{
    
    digitalWrite(ledPin,HIGH);
    Serial.println("me prendi");
    delay(tiempoOn);
    
    digitalWrite(ledPin,LOW);
    Serial.println("me apague");
    delay(tiempoOff);
   
}
```

### MORSE
¿Cómo hacer una A?

```
int ledPin = 13;
//establecemos los tiempos de nuestros caracteres
int tiempoPunto = 100;
int separador = 50;
int tiempoRaya = 500;
int finLetra = 100;

void setup()
{
    pinMode(ledPin,OUTPUT);
    //9600 es el baud rate
    //o tasa de baudios
    Serial.begin(9600);
}

void loop()
{
    //la A en morse .-
    //prendemos el punto
    digitalWrite(ledPin,HIGH);
    Serial.println("punto");
    //esperamos el punto encendido
    delay(tiempoPunto);
    //apagamos el punto
    digitalWrite(ledPin,LOW);
    //el espacio despues del punto
    delay(separador);
    
    //empezamos una raya
    digitalWrite(ledPin,HIGH);
    Serial.println("raya");
    //espero el tiempo de la raya
    delay(tiempoRaya);
    //apagamos la raya
    digitalWrite(ledPin,LOW);
    
    //cerramos la letra
    delay(finLetra);
}
```

# Encargo 3
debemos escribir el texto que escogimos en morse, a través del ledPin de nuestro arduino UNO.

```

