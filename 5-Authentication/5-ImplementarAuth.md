# Implementacion de Auth en Screens

> [!NOTE]
> Al implementar la siguiente logica, debes actualizar tus Screens, analiza cada cambio y adaptalo segun tu caso.

## Configuracion de `RegisterScreen.js`

**PASO 1:** agrega las referencias extras, de **AuthContext** y **Alert**.
```js
import { Alert } from 'react-native';
import { useAuth } from '../context/AuthContext';
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/637a57fc-5e4e-4b79-bc05-6d3dd764bce4" />

**PASO 2:** en el apartado de variables, define la function **`register`** del **AuthContext**.
```js
const { register } = useAuth();
```
<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/5bbaa3e2-34fd-4e10-9f29-5edab7df4940" />

**PASO 3:** actualiza tu function de **registrar** y adapta las _`validaciones`_ y los _`datos firestore`_ en la  logica.
```js
async function registrar() {
        //validar
        if (!nombre || !genero || !email || !clave || !confirmarClave) {
          Alert.alert( "Error", "Por favor, completa todos los campos obligatorios."); 
          return;
        }
        // Confirmar claves
        if (clave != confirmarClave) {
          Alert.alert( "Error", "Las contraseñas no coinciden" ); 
          return;
        }

        try {
          const data = {  nombre: nombre, genero: genero, };
          await register(email, clave, data);

        } catch (error) {
            console.error(error);
            if (error.code === "auth/email-already-in-use") {
                Alert.alert("Este correo electrónico ya está en uso.");
            } else if (error.code === "auth/weak-password") {
                Alert.alert("La contraseña debe tener al menos 6 caracteres.");
            } else {
                Alert.alert("Error al registrar la cuenta.");
            }
        }
    }
```
<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/c64d2940-fe64-4c3b-83b4-796d7f8103bf" />

**PASO 4:** asegurate de invocar tu function de **`registrar`** en el boton de accion. 

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/52fe27f7-c048-4d84-abb2-16e61a967670" />


## Configuracion de `LoginScreen.js`

**PASO 1:** agrega las referencias extras, de **AuthContext** y **Alert**.
```js
import { Alert } from 'react-native';
import { useAuth } from '../context/AuthContext';
```

<img width="1511" height="751" alt="image" src="https://github.com/user-attachments/assets/80849aa5-754c-4d7b-bb71-a0c05b236bd8" />

**PASO 2:** en el apartado de variables, define la function **`login`** del **AuthContext**.
```js
const { login } = useAuth();
```
<img width="1511" height="751" alt="image" src="https://github.com/user-attachments/assets/43e0dfe0-2a94-4d43-a899-1d5cd1c958bc" />

**PASO 3:** actualiza tu function de **entrar** y adapta las _`validaciones`_ en la logica.
```js
    async function entrar(){
        //validar
        if (!email || !clave) {
          Alert.alert( "Error", "Ingresa un email y contraseña" );
          return;
        }

        try {
            await login(email, clave);
        } catch (error) {
            Alert.alert("Error", "Error al iniciar sesión, verifica tus credenciales.");
        }
    }
```
<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/83047f95-af8f-434b-9f29-689ddfb52ce3" />

**PASO 4:** asegurate de invocar tu function de **`entrar`** en el boton de accion. 

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/ed566dd2-41d7-4bb5-8d32-02bf7f4185d0" />


## Configuracion de `ProfileScreen.js`

**PASO 1:** diseña un screen de perfil, para implementar el cierre de sesion.
```js
import { useState, useEffect } from 'react';
import { Layout, Input, ButtonRounded } from '../components';
import { Text, Alert, StyleSheet } from 'react-native';

export default function ProfileScreen({navigation}){

    return (
        <Layout>
            <Text style={styles.text}> Id:      </Text>
            <Text style={styles.text}> Nombre:  </Text>
            <Text style={styles.text}> Genero:  </Text>
            <Text style={styles.text}> Email:   </Text>
            <ButtonRounded title="Salir" isPrimary={false} />
        </Layout>
    );
}

const styles = StyleSheet.create({
  text: {
    textAlign: "justify",
    fontSize: 14,
    lineHeight: 22.5,
    marginBottom: 15,
  },
});
```

<img width="1664" height="820" alt="image" src="https://github.com/user-attachments/assets/3bb42a74-f1e0-4c6d-88bc-a2080b8533ca" />

**PASO 2:** agrega las referencias extras de **AuthContext** y **userService**.
```js
import { useAuth } from '../context/AuthContext';
import { obtenerUsuarioPorId } from '../services/userService';
```
<img width="1511" height="811" alt="image" src="https://github.com/user-attachments/assets/42436fa7-4b30-4103-9b4d-6b4147d9cb5b" />

**PASO 3:** crea las variables que se usaran en la logica.
```js
const [item, setItem] = useState(null);
const { user, logout } = useAuth();
```
<img width="1511" height="847" alt="image" src="https://github.com/user-attachments/assets/09e74b2f-12d5-482f-8425-5e3dd3b45768" />


**PASO 4:** crear tu function de **cargar** en la logica, este obtendra los datos del usuario guardados en firestore.
```js
  async function cargar(){
      try {
         const obj = await obtenerUsuarioPorId(user?.uid);
         setItem(obj);
      } catch (error) {
          Alert.alert("Error", "No se logro cargar el perfil");
      }
  }
```
<img width="1511" height="874" alt="image" src="https://github.com/user-attachments/assets/a993ac42-76f1-4b98-8aca-cbb7fc1ee3bd" />

**PASO 5:** crear un **useEffect** en la logica para actualizar los datos en la screen.
```js
useEffect(() => {
    cargar();
},[]);
```
<img width="1622" height="963" alt="image" src="https://github.com/user-attachments/assets/54f14c43-dd23-42a1-97f3-c04b2f692836" />

**PASO 6:** define los datos que mostraras en la screen de perfil.

> [!NOTE]
> El objeto `item` contiene **nombre, genero, email** y **uid**, datos almacenados en firestore.
```js
<Text style={styles.text}> Id:     {user?.uid}    </Text>
<Text style={styles.text}> Nombre: {item?.nombre} </Text>
<Text style={styles.text}> Genero: {item?.genero} </Text>
<Text style={styles.text}> Email:  {user?.email}  </Text>
```
<img width="1626" height="929" alt="image" src="https://github.com/user-attachments/assets/e4325903-1ed6-4a6b-b8e6-ebbfa2478e53" />

**PASO 7:** asegurate de invocar tu function de **`logout`** en el boton de accion. 

<img width="1626" height="929" alt="image" src="https://github.com/user-attachments/assets/f9dab7b6-a392-4641-b0a3-5c21e2e7eb2f" />

## Realizar pruebas de Authentication

Inicia tu app y accede desde **_Expo Go_**.

