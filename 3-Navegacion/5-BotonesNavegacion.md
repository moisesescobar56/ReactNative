# Botones de navegacion y acción en App 

**¿Como identificar un boton de navegación?**\
Un botón de navegación (Navigation Button) tiene como función principal llevar al usuario a una ubicación diferente dentro de la aplicación.

**¿Como identificar un boton de acción?**\
Un botón de acción (Action Button) tiene como función principal ejecutar una tarea/proceso o manipular datos en la pantalla actual.

## Ejemplos
<img width="945" height="816" alt="image" src="https://github.com/user-attachments/assets/07af0ae3-eee3-41e5-af69-edcac811b0f9" />

**Explicacion:**
- El boton `Entrar` debe validar credenciales en la base de datos y dependiendo si son correctas, dar acceso a la siguiente pantalla. **Funcion:** ejecutar proceso.
- El boton `Registrarse` debe redireccionar a la pantalla para registrarse. **Funcion:** navegar.

<img width="945" height="816" alt="image" src="https://github.com/user-attachments/assets/5a09bfee-5f7f-4ff5-a4c3-d89edce315c2" />


**Explicacion:**
- El boton `Confirmar` debe guardar al usuario en la base de datos, luego debe dar acceso a la siguiente pantalla. **Funcion:** ejecutar proceso.
- El boton `Iniciar sesion` debe redireccionar a la pantalla para autenticacion. **Funcion:** navegar.

# Implementar botones de navegacion y acción

**PASO 1:** abre una screen, en este caso `LoginScreen`.

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/9ae9a695-4dab-4a98-a770-f0d1ae2e4fec" />

**PASO 2:** inyecta el objeto `navigation` a la screen como parametro en la `function`.
```js
{ navigation }
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/ec3995fd-ae61-40b5-8a30-6e11368c4cac" />

**PASO 3:** implementar boton de **ACCION**, crea una `function` y agrega el evento `onPress` el boton correspondiente.

```js
function entrar(){
    // logica 
    navigation.navigate('NameRoute'); // ir a screen especifica
}
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/eb735dbe-70ba-4ddc-b578-6be534a0d3e9" />

> [!NOTE]
> El objeto `navigation` da acceso a functions como **`.navigate()`** y **`.goBack()`**\
> **`.navigate()`** se usa para ir a otra pantalla y **`.goBack()`** para regresar a la anterior.

**PASO 4:** implementar boton de **NAVEGACION**, agrega el evento `onPress` el boton correspondiente y usa `navigation.navigate()` para redireccionar al usuario a la screen.

```js
onPress={() => navigation.navigate('NameRoute') }
```

<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/0a181784-8274-4ada-8903-d413e6f34087" />

**PASO 5:** iniciar la app y verifica que funcionen los botones.

<img width="1437" height="816" alt="image" src="https://github.com/user-attachments/assets/f5a65664-04a8-4950-b085-bb2eed165ef5" />

