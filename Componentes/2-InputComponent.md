# Input component

## Crear componente

**PASO 1:** Crear el archivo `Input.js` js en la carpeta components:

<img width="1443" height="825" alt="image" src="https://github.com/user-attachments/assets/93a6fbba-f070-4936-94e2-5647d0c023d9" />

**PASO 2:** agrega las dependencias y crea la estructura del componente.
```js
import { TextInput, Text, View, StyleSheet } from "react-native";

export default function Input({ label, placeholder, type = "default", editable = true, lines = 1, value = "", onChangeText }){
    return (
        <View>
            <Text >{label}</Text>
            <TextInput 
                placeholder={placeholder}
                keyboardType= {type}
                editable = {editable}
                placeholderTextColor="#999"
                multiline={ lines > 1? true : false }
                numberOfLines= {lines}
                textAlignVertical="top"
                value={value}
                onChangeText={onChangeText}
             />
        </View>
    );
}
```

**PASO 3:** Crea el diseño del componente.
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
    control:{
        width: "100%",
        fontSize: 16,
        height: 45,
        borderColor: "#999",
        borderStyle: "solid",
        borderWidth: 1,
        padding: 10
    },
    textArea:{
        width: "100%",
        fontSize: 16,
        height: 120,
        borderColor: "#999",
        borderStyle: "solid",
        borderWidth: 1,
        padding: 10,
        justifyContent: "flex-start"
    }
});
```

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0deca28d-a4ac-4349-940d-af60b5903caa" />

**PASO 4:** Implementa el diseño del componente.

<img width="1820" height="898" alt="image" src="https://github.com/user-attachments/assets/efe1c4a8-58fb-494b-b4ca-275d711f99fc" />


## Implementar componente

**PASO 1:** exportar componente en el archivo `Components/index.js`.
```js
export { default as Input } from './Input';
```

<img width="1730" height="766" alt="image" src="https://github.com/user-attachments/assets/5a0ac217-f3f4-470c-8c35-403d069cde5a" />

**PASO 2:** agregar dependecias en `App.js`.

<img width="1730" height="766" alt="image" src="https://github.com/user-attachments/assets/14af7e50-c761-498b-a648-5a9df73ef3db" />

**PASO 3:** agregar implementacion del  componenten `Input`.

```js
<Input label="Email:" placeholder="name@mail.com" type="email-addres" />
<Input label="Asunto:" placeholder="Consulta" />
<Input label="Mensaje:" placeholder="Escribir aqui..." lines={4}/>
```

<img width="1730" height="766" alt="image" src="https://github.com/user-attachments/assets/354be50e-46a0-4d33-8468-dc4268e02c16" />

**PASO 4:** Iniciar la app y verificar que funcione.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f74ebf87-723f-47ea-bcbc-b16c140cfd69" />


## Tarea:
- Crear un componente llamado `ButtonPrimary` que reciba el `title` como parametro.
```js
<View>
    <Button title={title} color="#aaa" />
</View>
```

## Codigo completo:
```js
import { TextInput, Text, View, StyleSheet } from "react-native";

export default function Input({ label, placeholder, type = "default", editable = true, lines = 1, value = "", onChangeText }){
    return (
        <View style={styles.container}>
            <Text style={styles.label} >{label}</Text>
            <TextInput 
                placeholder={placeholder}
                keyboardType= {type}
                editable = {editable}
                style={ lines > 1? styles.textArea : styles.control }
                placeholderTextColor="#999"
                multiline={ lines > 1? true : false }
                numberOfLines= {lines}
                textAlignVertical="top"
                value={value}
                onChangeText={onChangeText}
             />
        </View>
    );
}

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
    control:{
        width: "100%",
        fontSize: 16,
        height: 45,
        borderColor: "#999",
        borderStyle: "solid",
        borderWidth: 1,
        padding: 10
    },
    textArea:{
        width: "100%",
        fontSize: 16,
        height: 120,
        borderColor: "#999",
        borderStyle: "solid",
        borderWidth: 1,
        padding: 10,
        justifyContent: "flex-start"
    }
});
```

