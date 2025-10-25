# Select (DropDownList) component

## Crear componente

**PASO 1:** abrir una terminal e instalar el paquete `Picker`.
```code
npx expo install @react-native-picker/picker
```

**PASO 2:** Crear el archivo `Select.js` js en la carpeta `components`:

<img width="1651" height="860" alt="image" src="https://github.com/user-attachments/assets/0b1a9697-19ec-43ac-96fd-5b43e21b76ad" />


**PASO 3:** agrega las dependencias y crea la estructura del componente.

```js
import React, { useState } from 'react';
import { View, Text, StyleSheet } from 'react-native';
import { Picker } from '@react-native-picker/picker';

export default function Select({ label, options, initialValue, onSelect }) {
  // valor seleccionado
  const [selectedValue, setSelectedValue] = useState(initialValue);

  // actualizar valor
  const handleChange = (itemValue) => {
    if (itemValue === 'placeholder') {
      onSelect(null);
      return; 
    }
    setSelectedValue(itemValue);
    if (onSelect) {
      onSelect(itemValue); 
    }
  };

  return (
    <View style={styles.container}>
      <Text style={styles.label}>{label}</Text>
      <View style={styles.pickerWrapper}>
        <Picker style={styles.picker} selectedValue={selectedValue} onValueChange={handleChange}>
          <Picker.Item label="SELECCIONAR" color="#999" value="placeholder" />
          {options.map((item) => (
            <Picker.Item 
              key={item.value} 
              label={item.label} 
              value={item.value} 
            />
          ))}
        </Picker>
      </View>
    </View>
  );
};
```

<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/20efd72c-a9b5-4f4c-9559-6625270b0eef" />


**PASO 4:** Crea el diseño del componente.
```js
const styles = StyleSheet.create({
  container:{
      width: "auto", 
      paddingHorizontal: 5,
      paddingBottom: 5,
      marginBottom: 5,
  },
  label:{
      fontSize: 14,
      fontWeight: "bold",
      color: "#000",
      marginBottom: 5
  },
  pickerWrapper: {
    borderWidth: 1,
    borderColor: '#999',
    overflow: 'hidden',
  },
  picker: {
    height: 55,
    width: '100%',
  },
});
```

<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/ea1f4715-9b40-4b22-ac2b-f62b39e23392" />



## Implementar componente

**PASO 1:** exportar componente en el archivo `Components/index.js`.
```js
export {default as Select } from './Select';
```

<img width="1647" height="856" alt="image" src="https://github.com/user-attachments/assets/a229e366-f14e-43f4-baeb-84051efa4c4d" />


**PASO 2:** agregar dependecias en la pantalla que se desea usar, ejemplo `RegisterScreen.js`.

<img width="1647" height="856" alt="image" src="https://github.com/user-attachments/assets/5f2febba-e8f3-4143-8186-a4fdd2d7b872" />

**PASO 3:** crear un `array` fuera de la screen, con las opciones que debe mostrar el `Select`.
```js
const GENEROS = [
  { label: "Femenino", value: "Femenino" },
  { label: "Masculino", value: "Masculino" },
];
```
<img width="1647" height="856" alt="image" src="https://github.com/user-attachments/assets/4bbf1557-09cc-4656-b85f-3873f1193dfb" />


**PASO 4:** agregar implementacion del  componente `Select`.

```js
<Select
    label="Seleccionar genero"
    options={GENEROS}
    initialValue={genero} // valor inicial
    onSelect={setGenero} // actualizar seleccion
/>
```


<img width="1931" height="1091" alt="image" src="https://github.com/user-attachments/assets/936cfaad-30b2-4f12-a342-3d6861c56854" />


**PASO 5:** Iniciar la app en **`Expo Go`** y verificar que funcione.


<img width="1121" height="737" alt="image" src="https://github.com/user-attachments/assets/eac5d4b9-12f2-4396-9038-c6a0fc3e5b5f" />

## Codigo completo:
```js
import React, { useState } from 'react';
import { View, Text, StyleSheet } from 'react-native';
import { Picker } from '@react-native-picker/picker';

export default function Select({ label, options, initialValue, onSelect }) {
  // valor seleccionado
  const [selectedValue, setSelectedValue] = useState(initialValue);

  // actualizar valor
  const handleChange = (itemValue) => {
    if (itemValue === 'placeholder') {
      onSelect(null);
      return; 
    }
    setSelectedValue(itemValue);
    if (onSelect) {
      onSelect(itemValue); 
    }
  };

  return (
    <View style={styles.container}>
      <Text style={styles.label}>{label}</Text>
      <View style={styles.pickerWrapper}>
        <Picker style={styles.picker} selectedValue={selectedValue} onValueChange={handleChange}>
          <Picker.Item label="SELECCIONAR" color="#999" value="placeholder" />
          {options.map((item) => (
            <Picker.Item 
              key={item.value} 
              label={item.label} 
              value={item.value} 
            />
          ))}
        </Picker>
      </View>
    </View>
  );
};

const styles = StyleSheet.create({
  container:{
      width: "auto", 
      paddingHorizontal: 5,
      paddingBottom: 5,
      marginBottom: 5,
  },
  label:{
      fontSize: 14,
      fontWeight: "bold",
      color: "#000",
      marginBottom: 5
  },
  pickerWrapper: {
    borderWidth: 1,
    borderColor: '#999',
    overflow: 'hidden',
  },
  picker: {
    height: 55,
    width: '100%',
  },
});
```

