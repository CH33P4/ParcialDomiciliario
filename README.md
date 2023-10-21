# Documentación
![Tinkercad](./img/ArduinoTinkercad.jpg)

## Integrantes 
- Matias A. Espinoza
- Tomas Zampella

## Proyecto: Contador binario.
![Proyecto](https://cdn.discordapp.com/attachments/1158565907921109100/1165369244909850735/image.png)

## Descripción
El proyecto consiste en una maqueta básica utilizando pocos componentes para llevar cuenta de números desde el 0 (cero) hasta el 99 (noventa y nueve) mediante la pulsación de botones: uno que incrementa el valor actual, otro que lo decrementa y un tercero cuya funcionalidad es retornar la cuenta nuevamente a cero.

## Función principal

Utilizamos los puertos analógicos A0 y A1 mediante #define para encender o apagar cada display según el número a representar en los mismos.

~~~ C (lenguaje en el que esta escrito)
void loop() {
  buttonUpState = digitalRead(plusOne); 
  buttonDownState = digitalRead(minusOne);
  resetButtonState = digitalRead(resetButton);
  if (buttonUpState != lastButtonUpState) {
    if (buttonUpState == HIGH) {
      if(counter < 9){
        counter++;    
      }
      if(counter == 9) {
        counter = 0;
        counter2++;
      }
      printOnSerial(counter, counter2);
      delay(200); 
   	}  
  }
  if (buttonDownState != lastButtonDownState) {
    if (buttonDownState == HIGH) {
      if(counter == 0 && counter2 == 1) {
        counter = 9; 
        counter2--;
      }
      if (counter == 0 && counter2 == 0){
        counter = 0;
      } 
      counter--;
      printOnSerial(counter, counter2);
      delay(200); 
    }
  } 
  if (resetButtonState != lastResetButtonState){
    if (resetButtonState == HIGH){
      counter = 0;
      counter2 = 0;
    }
  }
  showNumbers(counter, counter2);
} 

~~~
