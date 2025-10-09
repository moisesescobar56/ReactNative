# Introduccion App en React Native

## Requisitos
- Node.js ultima version (22.20.x) [Descargar](https://nodejs.org/es/download)
- NPM ultima version (11.6.X)
```code
npm install -g npm@latest
```
- Git x64 para control de versiones [Descargar](https://git-scm.com/downloads/win)
- Vs Code o cualquier otro [Descargar](https://code.visualstudio.com/download)

## Expo React Native

¿Qué es Expo?
- Expo es un conjunto de herramientas que facilita el desarrollo con React Native, incluyendo:
- Servidor de desarrollo rápido.
- Posibilidad de probar apps en móvil, emulador o navegador web.
- Instalación sencilla de dependencias y librerías.

**Descargar Expo Go**

<img width="100" height="100" alt="image" src="https://github.com/user-attachments/assets/4a47c0c3-cebe-4c4d-9e7a-d98cc4c20b5c" />

[Descargar Play Store](https://play.google.com/store/apps/details?id=host.exp.exponent&hl=es_SV)

## Crear App con Expo

**PASO 1:** acceder a la carpeta de proyectos.

<img width="1123" height="633" alt="image" src="https://github.com/user-attachments/assets/e0445d85-ec78-4553-a91d-ea00df0faf53" />

**PASO 2:** editar la ruta, escribir "cmd" y pulsar **Enter**.

<img width="1122" height="632" alt="image" src="https://github.com/user-attachments/assets/b5a3f02b-eedf-4900-b49f-15a9adda1a4c" />

**Resultado:**

<img width="1054" height="426" alt="image" src="https://github.com/user-attachments/assets/105c1686-c1f6-4fe8-9e15-05df0878fd56" />

**PASO 3:** escribir los comandos en el cmd y pulsar **Enter**.

```code
npx create-expo-app@latest AppIntro --template blank
```
<img width="1053" height="192" alt="image" src="https://github.com/user-attachments/assets/bdad7bb6-906d-4d05-a867-0a9bb839706d" />

- **npx:** permite usar paquetes de npm sin instalarlos globalmente.
- **@latest:** instala la ultima version del paquete.
- **"AppIntro":** nombre asignado a la app.
- **"-- template blank":** plantilla en blanco o vacia.

**Esperar termine el proceso:**

<img width="1054" height="426" alt="image" src="https://github.com/user-attachments/assets/88e24d42-e9b9-4bae-8822-dfd864b058d8" />

<img width="1054" height="426" alt="image" src="https://github.com/user-attachments/assets/02e26ca5-f3e7-41aa-b9f1-7aeb37752e1c" />

**PASO 4:** acceder a la nueva carpeta e instalar las dependencias web.
```code
cd AppIntro
```
```code
npx expo install react-dom react-native-web
```
<img width="1053" height="448" alt="image" src="https://github.com/user-attachments/assets/e8cf3adf-5885-4b47-85fb-0b5e75130665" />


**PASO 5:** abrir la app en VS Code.
```code
code .
```

<img width="1053" height="448" alt="image" src="https://github.com/user-attachments/assets/e0f36cc9-cd85-41e4-a303-066868c598b3" />

**PASO 6:** Dar click en **"Yes, I trust the authors"**.

<img width="1800" height="1020" alt="image" src="https://github.com/user-attachments/assets/76fd11c9-af6a-40f9-b7c3-087966cceebd" />

**Resultado:**

<img width="1574" height="690" alt="image" src="https://github.com/user-attachments/assets/46b1eb23-0c82-41c3-9798-3418e1007c09" />

**PASO 7:** activa NPM Scripts.

<img width="1573" height="690" alt="image" src="https://github.com/user-attachments/assets/207a84b7-6e53-4fbb-b7f0-28ca4480eb24" />

**PASO 8:** ejecuta la App en modo web.

<img width="1573" height="690" alt="image" src="https://github.com/user-attachments/assets/3d988130-853d-4ce1-8eab-4bb506a82f8c" />

**Resultado:**
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/8fc3f9c6-32f9-48d6-8bba-8e59a43f8190" />

**PASO 9:** actualiza el archivo **App.js** y coloca **"Hola Mundo"**.

<img width="1918" height="1018" alt="image" src="https://github.com/user-attachments/assets/277608a8-7d3b-4e27-a7a8-4f0cefc14d41" />


**Resultado:**

<img width="1918" height="1017" alt="image" src="https://github.com/user-attachments/assets/a72abac7-5b54-4f8a-8311-c3b13ad2fa75" />
