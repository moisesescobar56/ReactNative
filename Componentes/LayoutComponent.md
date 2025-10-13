# Layout Component

**¿Que es un componenten en React Native?**

Un **`componente`**  es la unidad básica de construcción de una interfaz de usuario (UI).
Piensa en él como una pieza reutilizable que define cómo se muestra y cómo se comporta una parte de tu aplicación.

**En palabras simples:** Un componente es como un bloque de Lego, puedes combinar varios para construir toda tu aplicación.

**Por ejemplo:**

- Un botón → es un componente.
- Una caja de texto → también es un componente.
- Una pantalla completa con varios elementos → también puede ser un componente.

**Componentes básicos (nativos):**
- `<View>` → contenedor, como un “div” en HTML.
- `<Text>` → muestra texto.
- `<Button>` → botón.
- `<TextInput>` → campo de entrada de texto.
- `<ScrollView>`, `<Image>`

## Crear componente personalizado

**PASO 1:** Abrir una terminal e instalar Safe Area Context.
```code
npm install react-native-safe-area-context
```

<img width="1507" height="815" alt="image" src="https://github.com/user-attachments/assets/b03d4198-18f3-4c68-a729-cf7ada765259" />


**PASO 2:** Crear 2 archivos js en la carpeta components:
- index.js
- Layout.js

<img width="1507" height="815" alt="image" src="https://github.com/user-attachments/assets/403cba35-bbe8-4991-8c8e-d1c3117d04b6" />

**PASO 3:** agregar las dependencias del componente.
```js
import { StyleSheet, Text,StatusBar, View } from 'react-native';
import {SafeAreaView, SafeAreaProvider} from 'react-native-safe-area-context';
```
<img width="1699" height="815" alt="image" src="https://github.com/user-attachments/assets/0e7dfaa6-ace4-4a92-bfd3-3e2b278e615a" />

**PASO 4:** configurar el componente con su function base con el mismo nombre del archivo.

<img width="1706" height="815" alt="image" src="https://github.com/user-attachments/assets/c4167935-6726-4016-9c44-3deb76e505fa" />

**PASO 5:** agregar la estructura de contenido.

<img width="1706" height="815" alt="image" src="https://github.com/user-attachments/assets/5d51f88c-b4f0-4d4e-9b18-aaaf28ec6be4" />

## Diseño de componente

**PASO 1:** crear el objeto de estilos.
```js
const styles = StyleSheet.create({

});
```

<img width="1706" height="815" alt="image" src="https://github.com/user-attachments/assets/71fded2b-1e3f-4c3c-9c61-ee1b563e45c5" />

**PASO 2:** crear los estilos container, title y body.
```js
container: {
  flex: 1, // Ocupa todo el espacio.
  backgroundColor: "#f5f5f5", // Fondo gris claro.
  justifyContent: "center", // Centra el contenido verticalmente.
  alignItems: "center", // Centra el contenido horizontalmente.
},
title: {
  color: "#000", // Texto blanco.
  fontSize: 20, // Tamaño de fuente grande.
  fontWeight: "bold", // Texto en negrita.
  paddingVertical: 10, // relleno
},
body: {
  flex: 1, // Ocupa el espacio restante.
  justifyContent: "top", // Alinea el contenido arriba.
  alignItems: "left", // Alinea el contenido a la izquierda.
  padding: 5, // Agrega un relleno de 5px.
},
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/585d084f-c726-414c-baec-b7a84a6ca703" />

**PASO 3:** implementar los estilos en el contenido.

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/06a5c514-5282-49de-a417-7e3dff9b89b4" />

**PASO 4:** abrir el archivo `Components/index.js` y exportar el componente.
```js
export { default as Layout } from './Layout';
```

<img width="1710" height="819" alt="image" src="https://github.com/user-attachments/assets/bd955fde-48e5-4d48-b9dc-c25f79d5984a" />

## Implementar componente

**PASO 1:** abrir el archivo `App.js` e importar el nuevo componente.
```js
import { Layout } from './components';
```

<img width="1706" height="815" alt="image" src="https://github.com/user-attachments/assets/762d3790-849e-46ea-8e68-1a2551804bcf" />

**PASO 2:** implementar el componente `Layout`.
```js
<Layout title="Contacto" >
  
</Layout>
```

<img width="1706" height="815" alt="image" src="https://github.com/user-attachments/assets/c30a9c3c-dedd-4427-a0b2-9e8aa2716960" />

**PASO 3:** iniciar la app y verificar resultado.

<img width="1926" height="1029" alt="image" src="https://github.com/user-attachments/assets/70da5ba4-ec6f-410d-bedb-5467942bc0b3" />



