


-------Consigna Trabajo Dojo 1------	

Realizar el circuito en TinckerCad para simular el semáforo y desarrollar el codigo fuente para
su funcionamiento correcto.


```
#define Led_Red1 12
#define Led_Red2 12
#define Led_Yellow1 10
#define Led_Yellow2 10
#define Led_Green1 9
#define Led_Green2 9
#define Buzzer 7

void setup()
{
  pinMode(Led_Red1, OUTPUT);
  pinMode(Led_Red2, OUTPUT);
  pinMode(Led_Yellow1, OUTPUT);
  pinMode(Led_Yellow2, OUTPUT);
  pinMode(Led_Green1, OUTPUT);
  pinMode(Led_Green2, OUTPUT);
  pinMode(Buzzer, OUTPUT);
}


void loop()
{

  prendeYApagaLed(Led_Red1, 0, 0, 1, 15, 1000, 1000, 2000);
  prendeYApagaLed(Led_Yellow1, 0, 0, 1, 2, 2000, 1000, 500);
  prendeYApagaLed(Led_Green1, 25000, 20000, 1, 0, 0, 100, 0);		
}		
  
void prendeYApagaLed(int led, int tiempo,int tiempo_Sumar, int cantidadRepeticiones, int cant_sonar, int tiempo_Low, float tiempo_High, int volumen)
{
  
  for (int i=0; i < cantidadRepeticiones;i++)
  {
  	digitalWrite(led,HIGH);
    power_buzzer(cant_sonar, tiempo_High, tiempo_Low, volumen);
    delay(tiempo);
    delay(tiempo_Sumar);
    digitalWrite(led, LOW);
    delay(500);
  }
}

void power_buzzer(int cant_sonar, float tiempo_High, int tiempo_Low, int volumen)
{
  for (int i = 0; i < cant_sonar; i++) {
  	tone(Buzzer, volumen);// Frecuencia del tono
  	delay(tiempo_High);// Duración del tono
  	noTone(Buzzer); // Detener el tono
  	delay(tiempo_Low);// tiempo de espera antes de repetir el proceso
  }
}
```