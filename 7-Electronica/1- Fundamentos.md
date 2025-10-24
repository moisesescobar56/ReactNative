
# Fundamentos de Electrónica: Del Concepto al Control con Arduino

## 1\. Conceptos Breves de Electrónica

Aprenderás a manejar la electricidad de la misma manera que el agua: tiene un flujo, una presión y una resistencia.

| Concepto | Símbolo | Unidad de Medida | Analogía del Agua | Definición Breve |
| :--- | :--- | :--- | :--- | :--- |
| **Voltaje** | V | Voltios (V) | Presión del agua | La **fuerza** que impulsa a los electrones. |
| **Corriente** | I | Amperios (A) | Flujo o caudal | El **flujo** de electrones a través de un circuito. |
| **Resistencia** | R | Ohmios ($\Omega$) | Tubería estrecha/Válvula | La **oposición** al flujo de corriente. |
| **Ley de Ohm** | | | | La relación fundamental: **$V = I \times R$** |

### 1.1 Diodo LED

<img width="617" height="275" alt="image" src="https://github.com/user-attachments/assets/0eaa13b0-2426-42b2-b028-26ff98a05cb3" />

### 1.2 Calculo de resistencias

<img width="546" height="432" alt="image" src="https://github.com/user-attachments/assets/965779ae-4e9a-4548-a5d4-6465c9401b69" />


### 1.3 Breadboard

<img width="1200" height="441" alt="image" src="https://github.com/user-attachments/assets/c37c0db0-974b-4777-8d7a-dca4358ff54f" />

### 1.4 Arduino

<img width="1200" height="1200" alt="image" src="https://github.com/user-attachments/assets/f7c36740-8cbf-4caf-ab28-f6ee19e76934" />

-----

## 2\. Encender un LED en un Protoboard (Circuito Básico)

El objetivo de este ejercicio es encender el LED de forma segura, usando una resistencia para evitar que se queme con el voltaje de la fuente.

### 2.1 Componentes Necesarios

  * 1 LED (cualquier color).
  * 1 Resistencia (**$220\ \Omega$** o **$330\ \Omega$**).
  * 1 Protoboard.
  * Cables de conexión (*Jumpers*).
  * Fuente de Poder (ejemplo: 5V de Arduino o una batería).

### 2.2 Diagrama de Conexión

1.  **Conexión de la Resistencia:** Conecta un extremo de la resistencia a la línea de **GND** (negativo) de la protoboard.
2.  **Conexión del LED:**
      * Conecta el **Cátodo** (pata corta) del LED al otro extremo de la resistencia.
      * Conecta el **Ánodo** (pata larga) del LED a una columna libre del centro de la protoboard.
3.  **Conexión a la Fuente:**
      * Conecta **GND** (Tierra/Negativo) de la fuente a la línea GND de la protoboard.
      * Conecta **+5V** (Positivo) de la fuente a la columna donde está el Ánodo del LED.
  
  <img width="912" height="577" alt="image" src="https://github.com/user-attachments/assets/b43cf497-ea61-47c7-ae43-0042fa1b041a" />


> [!WARNING]
> **¡Advertencia\!** Nunca conectes el LED directamente a la fuente de poder sin una resistencia. Se quemará inmediatamente.


## 3\. Encender y Apagar un LED Mediante Arduino (Salida Digital)

Ahora usaremos la placa Arduino para automatizar el encendido y apagado del LED a través de código. Este es el famoso proyecto **"Blink"**.

### 3.1 Componentes Requeridos

  * **Placa Arduino Uno R3** (o similar).
  * Los componentes del circuito anterior (LED, Resistencia, Protoboard).
  * Cable USB.

### 3.2 Montaje del Circuito con Arduino

En lugar de usar la línea de +5V de la protoboard, usaremos un pin digital de Arduino que podemos controlar por software.

1.  **Mantén el circuito anterior** (LED y Resistencia).
2.  **Conecta la Tierra:** Conecta el extremo de la resistencia (Cátodo del LED) al pin **GND** (Tierra) del Arduino.
3.  **Conecta la Señal:** Conecta el **Ánodo** (pata larga) del LED al **Pin Digital 13** del Arduino.

<img width="1731" height="797" alt="image" src="https://github.com/user-attachments/assets/107692d4-d97b-49b8-9338-d83fc4a61e96" />


### 3.3 El Código "Blink" en Arduino IDE

Copia este código, súbelo a tu placa Arduino y observa cómo el LED parpadea.

```cpp
// 1. ASIGNACIÓN DE PIN: Define el pin que vamos a usar
const int LED_PIN = 13;

// 2. FUNCIÓN SETUP: Se ejecuta una sola vez al inicio
void setup() {
  // Configura el pin 13 como una SALIDA (OUTPUT)
  pinMode(LED_PIN, OUTPUT);
}

// 3. FUNCIÓN LOOP: Se repite infinitamente
void loop() {
  // ACCIÓN 1: ENCENDER el LED
  digitalWrite(LED_PIN, HIGH);
  
  // ESPERA 1 segundo (1000 milisegundos)
  delay(1000);
  
  // ACCIÓN 2: APAGAR el LED
  digitalWrite(LED_PIN, LOW);
  
  // ESPERA 1 segundo (1000 milisegundos)
  delay(1000);
}
```

#### ✅ Pasos Finales

1.  Abre el **Arduino IDE**.
2.  Copia y pega el código.
3.  Conecta tu Arduino por USB.
4.  Selecciona la placa y el puerto correcto en el menú **Herramientas**.
5.  Haz clic en el botón **Subir** (Upload).

**¡Felicidades\!** Has programado con éxito tu primer circuito, controlando una salida digital (el LED) desde tu placa Arduino.
