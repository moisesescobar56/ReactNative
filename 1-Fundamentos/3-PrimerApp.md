# App Calculadora

## Estructura de archivos

**PASO 1:** crear las carpetas escenciales.
- api
- components
- screens
- services

<img width="1476" height="690" alt="image" src="https://github.com/user-attachments/assets/40b94e21-7a24-4283-b1b6-54eba45c833a" />

**Resultado:**

<img width="1476" height="690" alt="image" src="https://github.com/user-attachments/assets/166bb366-550c-47d6-9988-01fc34e91998" />

**PASO 2:** crear una nueva screen llamada **"CalculadoraScreen.js"** en la carpeta **"screens"**.

<img width="1476" height="690" alt="image" src="https://github.com/user-attachments/assets/e50a9f4b-accb-45fe-9fc1-8833c57375a2" />

**Resultado:**

<img width="1476" height="690" alt="image" src="https://github.com/user-attachments/assets/02ad0de0-3d49-4454-94fe-a604f1f614b5" />

**PASO 3:** agregar las dependencias necesarias.
```js
import { useState } from "react";
import { View, Text, TextInput, Button, StyleSheet } from "react-native";
```

<img width="1599" height="643" alt="image" src="https://github.com/user-attachments/assets/2922ae39-06fe-4770-8394-94b9b18c15fe" />

**PASO 4:** crear la **function** base para exportar el Screen.
```js
export default function CalculadoraScreen(){
    return(
        <View>
            
        </View>
    );
}
```
<img width="1598" height="642" alt="image" src="https://github.com/user-attachments/assets/df0c9c01-471f-4d81-bb24-7f6243097931" />

**PASO 5:** agregar la estructura de diseño de la screen.

```js
<TextInput 
    keyboardType="numeric"
    placeholder="Primer numero" />
<TextInput 
    keyboardType="numeric"
    placeholder="Segundo numero" />
<Button
    color="#555" 
    title="Calcular" />
<Text>Resultado: </Text>
```

<img width="1598" height="785" alt="image" src="https://github.com/user-attachments/assets/3b373f0a-3646-4922-bed0-faa14be0bba5" />

**PASO 6:** abrir el archivo App.js y eliminar las etiquetas y estilos.

<img width="1598" height="785" alt="image" src="https://github.com/user-attachments/assets/4ae25fb2-b66e-4070-8f45-f15501ea16d0" />

**PASO 7:** agrega las dependencias de _**CalculadoraScreen.js**_ e implementalo como un componente.

<img width="1598" height="785" alt="image" src="https://github.com/user-attachments/assets/83de320e-5671-49f8-a3fe-fe88a766c60a" />

**PASO 8:** ejecutar y verificar que muestre un resultado.

<img width="1918" height="1023" alt="image" src="https://github.com/user-attachments/assets/20f89434-1196-4d8f-9dff-b87db7e1235f" />


## Diseño de screen
Se usara la dependencia agregada anteriormente **StyleSheet** para crear un objeto de estilos.

**PASO 1:** crear una variable con una instancia a **StyleSheet**.
```js
const styles = StyleSheet.create({
    
});
```
<img width="1598" height="785" alt="image" src="https://github.com/user-attachments/assets/0202791d-97ff-4705-ae51-6ee3e813f962" />

**PASO 2:** crear una regla.
```js
container: {
    flex: 1,
    backgroundColor: '#fff',
    justifyContent: 'center',
    padding: 24
  },
```

<img width="1598" height="785" alt="image" src="https://github.com/user-attachments/assets/bb92e9c5-ca7b-49ed-a9b6-7a397879b1f0" />


| Propiedad                      | Descripción                                                                                                     |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------- |
| **`flex: 1`**                  | Hace que el contenedor ocupe **todo el espacio disponible** en la pantalla. Se usa dentro de layouts flexibles. |
| **`backgroundColor: "#fff"`**  | Establece el color de fondo del contenedor en **blanco**.                                                       | 
| **`justifyContent: "center"`** | Centra **verticalmente** los hijos dentro del contenedor (en el eje principal del flexbox).                     | 

**PASO 3:** implementar el estilo al control **View** y verificar el resultado.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/59ac9431-4ce0-4b2d-93d3-549ff0f58390" />

**NOTA:** mantener en ejecucion la app para ir viendo los resultados.

**PASO 4:** crear estilos para los inputs y text.
```js
input: {
    borderWidth: 1,
    borderColor: "#D1D5DB",
    padding: 10,
    borderRadius: 8,
    marginBottom: 12,
    fontSize: 16,
    backgroundColor: "#FFF",
  },
  text: {
    marginTop: 20,
    fontSize: 20,
    textAlign: "justify",
    color: "#000",
  }
```

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/aa7944c7-968f-4f3c-9a86-f951c9ce5faf" />

**PASO 5:** implementar el estilo a los **TextInput** y **Text**, verificar el resultado.

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/47b4d63d-f82f-4011-88f6-179b7caac796" />

**NOTA:** mantener en ejecucion la app para ir viendo los resultados.

## Implementar funcionalidad

**¿Qué es useState()?**

**`useState`** es una función de `React` que permite a los componentes guardar y actualizar valores (su estado interno).
Cada vez que el valor cambia, el componente se vuelve a `renderizar` automáticamente para mostrar los nuevos datos.

**PASO 1:** Analizar y definir las variables a utilizar.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bbae16be-9cd9-4ad2-baeb-7022c3fec534" />

| Elemento                 | Función                                         |
| ------------------------ | ----------------------------------------------- |
| **`variable`**               | Guarda el **valor actual** del estado.          |
| **`setVariable`**            | Es una **función** que **actualiza** ese valor. |
| **`useState(valorInicial)`** | Define el valor inicial del estado.             |

**PASO 2:** implementar la lectura y actualizacion de las variables.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/98f43c29-9c09-4053-a5e8-e18a03c321bd" />


**PASO 3:** crear la `function` que ejecutara el **Button** al ser presionado.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/978402a3-4c4f-41e9-8e7c-81d51e354a07" />

**PASO 4:** implementar la llamada de la `function` **calcular** en el **Button**.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bc2d4d8c-9d35-4b9a-9044-e6da5f9b8805" />


- **Propiedad `onPress`:** en React Native se usa para detectar cuando el usuario toca o presiona un elemento (como un botón, texto o imagen).

**PASO 5:** Probar el funcionamiento de la calculadora.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/37d0974c-fb34-4239-bc39-7d72455cf378" />






