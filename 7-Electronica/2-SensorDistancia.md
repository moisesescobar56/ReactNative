# PRÁCTICA: MEDICIÓN DE DISTANCIA CON HC-SR04 Y ARDUINO

**OBJETIVO:** Usar el sensor ultrasónico HC-SR04 para medir la distancia y mostrar el resultado en el Monitor Serial.

## 1. COMPONENTES NECESARIOS:
* Placa Arduino Uno R3.
* Sensor Ultrasónico HC-SR04.
* Protoboard y cables.

## 2. MONTAJE DEL CIRCUITO (HARDWARE):
Conexiones del Sensor al Arduino:
| Pin del HC-SR04 | Pin del Arduino |
|-----------------|-----------------|
| VCC             | 5V              |
| GND             | GND             |
| Trig            | Pin Digital 9   |
| Echo            | Pin Digital 10  |

<img width="937" height="452" alt="image" src="https://github.com/user-attachments/assets/e41a96a9-b78f-4b37-b5dc-377496294f27" />


## 3. CÓDIGO ARDUINO (SKETCH):
```cpp
// Definición de Pines para el sensor
const int TRIG_PIN = 9;  // Pin de Disparo (OUTPUT)
const int ECHO_PIN = 10; // Pin de Recepción (INPUT)

// Variables para el cálculo
long duracion; // Tiempo de eco en microsegundos
int distancia_cm; // Distancia calculada

// FUNCIÓN SETUP: Se ejecuta una sola vez al inicio
void setup() {
  pinMode(TRIG_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);

  // Inicializa la comunicación serial a 9600 baudios
  Serial.begin(9600);
  Serial.println(">>> Monitor Serial Activado <<<");
}

// FUNCIÓN LOOP: Se repite continuamente
void loop() {
  // 1. Limpiar y enviar un pulso corto (Trigger)
  digitalWrite(TRIG_PIN, LOW);
  delayMicroseconds(2); 
  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW); 

  // 2. Medir la duración del pulso de retorno (Echo)
  duracion = pulseIn(ECHO_PIN, HIGH);

  // 3. Calcular la Distancia: Tiempo / 58 (para centímetros)
  distancia_cm = duracion / 58; 

  // 4. Mostrar Resultados
  Serial.print("Distancia: ");
  Serial.print(distancia_cm);
  Serial.println(" cm");

  // Pausa de 500ms antes de la siguiente medición
  delay(500);
}
```

## 4. VERIFICACIÓN:
1. Sube el código a tu placa Arduino.
2. Abre el Monitor Serial (asegúrate de que la velocidad sea 9600 baudios).
3. Mueve un objeto frente al sensor y observa los valores de distancia.

<img width="1871" height="861" alt="image" src="https://github.com/user-attachments/assets/8471e3f4-2978-4feb-bf10-f46004c3fc2a" />
