# Button Rounded component

## Crear componente

**PASO 1:** Crear el archivo `ButtonRounded.js` js en la carpeta `components`:

<img width="1711" height="821" alt="image" src="https://github.com/user-attachments/assets/1ef1387d-a4bf-4e2c-827e-171950d5516d" />

**PASO 2:** agrega las dependencias y crea la estructura del componente.
```js
import React from "react";
import { TouchableOpacity, Text, StyleSheet } from "react-native";

export default function ButtonRounded({ title, onPress, isPrimary = true }) {

  return (
    <TouchableOpacity
      onPress={onPress}
      activeOpacity={0.8}
    >
      <Text>
        {title}
      </Text>
    </TouchableOpacity>
  );
}
```

<img width="1776" height="850" alt="image" src="https://github.com/user-attachments/assets/1b11453a-7db7-471a-9750-7aad521cf921" />


**PASO 3:** Crea el diseño del componente.
```js
const styles = StyleSheet.create({
  button: {
    paddingVertical: 12,
    paddingHorizontal: 20,
    borderRadius: 25,
    alignItems: "center",
    justifyContent: "center",
    marginVertical: 8,
    elevation: 3,
    shadowColor: "#000",
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.2,
    shadowRadius: 3,
  },
  primary: {
    backgroundColor: "#2563EB", // azul
  },
  secondary: {
    backgroundColor: "#FFF",
    borderWidth: 1.5,
    borderColor: "#2563EB",
  },
  text: {
    fontSize: 16,
    fontWeight: "600",
  },
  textPrimary: {
    color: "#FFF",
  },
  textSecondary: {
    color: "#2563EB",
  },
});

```

<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/7b372e1a-4057-40f3-bad0-2ef9c4b229b1" />



**PASO 4:** Implementar el diseño del componente.

**<TouchableOpacity></TouchableOpacity>**
```js
style={[ styles.button, isPrimary ? styles.primary : styles.secondary, ]}
```

**<Text></Text>**
```js
style={[ styles.text, isPrimary ? styles.textPrimary : styles.textSecondary, ]}
```

<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/d86daa2b-fd3f-49ff-858a-59db480d9cc9" />



## Implementar componente

**PASO 1:** exportar componente en el archivo `Components/index.js`.
```js
export {default as ButtonRounded } from './ButtonRounded';
```

<img width="1776" height="850" alt="image" src="https://github.com/user-attachments/assets/8fa08dfa-4e37-4efb-83b2-cbe7bcaeaa13" />


**PASO 2:** agregar dependecias en `App.js`.

<img width="1776" height="850" alt="image" src="https://github.com/user-attachments/assets/2ac0aece-c210-4f1a-b951-30b52f8fb1fe" />


**PASO 3:** agregar implementacion del  componenten `Input`.

**Primary**
```js
<ButtonRounded
  title="Enviar"
  onPress={() => Alert.alert('Enviado', 'Mensaje enviado correctamente')}
/>
```

**Secondary**
```js
<ButtonRounded
  title="Cancelar"
  isPrimary={false}
  onPress={() => Alert.alert('Cancelado', 'Envio cancelado')}
/>
```

<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/b474fcd2-72b3-4026-b1fa-03a2be3929f9" />


**PASO 4:** Iniciar la app en **`Expo Go`** y verificar que funcione.

<img width="2376" height="1257" alt="image" src="https://github.com/user-attachments/assets/bb5d1a47-608f-438a-bc87-a2e786582d37" />


## Codigo completo:
```js
import React from "react";
import { TouchableOpacity, Text, StyleSheet } from "react-native";

export default function ButtonRounded({ title, onPress, isPrimary = true }) {

  return (
    <TouchableOpacity
      onPress={onPress}
      activeOpacity={0.8}
      style={[ styles.button, isPrimary ? styles.primary : styles.secondary, ]}
    >
      <Text
        style={[ styles.text, isPrimary ? styles.textPrimary : styles.textSecondary, ]}
      >
        {title}
      </Text>
    </TouchableOpacity>
  );
}

const styles = StyleSheet.create({
  button: {
    paddingVertical: 12,
    paddingHorizontal: 20,
    borderRadius: 25,
    alignItems: "center",
    justifyContent: "center",
    marginVertical: 8,
    elevation: 3,
    shadowColor: "#000",
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.2,
    shadowRadius: 3,
  },
  primary: {
    backgroundColor: "#2563EB", // azul
  },
  secondary: {
    backgroundColor: "#FFF",
    borderWidth: 1.5,
    borderColor: "#2563EB",
  },
  text: {
    fontSize: 16,
    fontWeight: "600",
  },
  textPrimary: {
    color: "#FFF",
  },
  textSecondary: {
    color: "#2563EB",
  },
});
```


