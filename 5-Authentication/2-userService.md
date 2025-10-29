# Crear servicio de usuarios

## Crear `userService.js`

**PASO 1:** crea un nuevo archivo en la carpeta **📁services** llamdado `userService.js`.

```code
userService.js
```

<img width="1511" height="751" alt="image" src="https://github.com/user-attachments/assets/16914c62-d711-422e-8fd9-2e24361c3595" />

**PASO 2:** agrega la siguiente logica al archivo `userService.js` y **guarda** los cambios.

```js
import { db } from '../api/firebase';
import {  doc, setDoc, getDoc } from 'firebase/firestore';

const usuariosRef = "usuarios";

export function agregarUsuario(uid, userData) {
  // 'uid' es el ID del documento
  const userDocRef = doc(db, usuariosRef, uid);
  return setDoc(userDocRef, userData);
};

export async function obtenerUsuarioPorId(uid) {
  const userDocRef = doc(db, usuariosRef, uid);
  const docSnap = await getDoc(userDocRef);

  if (docSnap.exists()) {
    return docSnap.data();
  } else {
    // El documento no existe
    console.warn("No se encontró el perfil de usuario en Firestore para el UID:", uid);
    return null;
  }
};
```

## Explicacion del userService.js

1. agregar importanciones necesarias.
<img width="816" height="69" alt="image" src="https://github.com/user-attachments/assets/e4ccb13e-39f2-4ab0-957d-253df424847a" />

2. function para crear documento con id especifico en una collection.
<img width="1106" height="224" alt="image" src="https://github.com/user-attachments/assets/2e394616-dc12-4a92-9dfa-e86888d6a15a" />

3. function para obtener por id a un usuario de la collection.
<img width="1187" height="380" alt="image" src="https://github.com/user-attachments/assets/3fd213d9-8f68-49dc-ab8a-bd4b7228a2f1" />

5. 
