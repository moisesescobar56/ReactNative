# Crear AuthContext 

Un `AuthContext` es un Context específico para manejar la autenticación de usuarios.

Suele incluir:
- El usuario actual (**user**).
- Un loading para saber si aún se está validando la sesión.
- Funciones de **`login`**, **`register`** y **`logout`**.

## Analisis

Es importante identificar los datos que se almacenan en tu registro, dado que esos datos se usaran en la `function` de **register** del **`AuthContext`**.

Al usar **Authentication** de Firebase, las credenciales se guardaran en ese servicio, asi quedaran distribuidos los datos:
- nombre (**Firestore**)
- genero (**Firestore**)
- email (**Authentication**)
- clave/password (**Authentication**)

<img width="456" height="809" alt="image" src="https://github.com/user-attachments/assets/f6b60b53-683a-452b-b3fa-811293e72b30" />


## Configuracion de AuthContext

**PASO 1:** en la raiz del proyecto crea una 📁carpeta llamada **`context`**.
```code
context
```
**PASO 2:** crea un nuevo archivo llamado **`AuthContext.js`** en la carpeta **context**

```code
AuthContext.js
```

<img width="1511" height="751" alt="image" src="https://github.com/user-attachments/assets/88fec90b-d894-4478-82b6-baff92ad577e" />

**PASO 3:** agrega la siguiente logica a tu **`AuthContext.js`** y guarda los cambios.

```js
import React, { createContext, useState, useEffect, useContext } from 'react';
import { onAuthStateChanged, createUserWithEmailAndPassword, signInWithEmailAndPassword, signOut } from 'firebase/auth';
import { auth } from '../api/firebase';
import { agregarUsuario } from '../services/userService';

// 1. Crear el contexto
const AuthContext = createContext();

// 2. Crear el Proveedor (Provider)
export const AuthProvider = ({ children }) => {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);

  // 3. Listener de Firebase para el estado de autenticación
  useEffect(() => {
    const unsubscribe = onAuthStateChanged(auth, (authUser) => {
      // Si authUser existe, ponlo en el estado 'user', si no, 'user' será null
      setUser(authUser);
      setLoading(false);
    });

    // Función de limpieza para desuscribirse del listener
    return () => unsubscribe();
  }, []);

  // 4. Funciones de autenticación
  const login = (email, password) => {
    return signInWithEmailAndPassword(auth, email, password);
  };

  const register = async (email, password, data) => {
    try {
      // 1. Crear el usuario en Firebase Authentication
      const userCredential = await createUserWithEmailAndPassword(auth, email, password);
      const authUser = userCredential.user;

      // 2. Crear el documento de usuario en Firestore
      // Usamos el UID de Authentication como ID del documento en Firestore
      const userData = {
        uid: authUser.uid,
        email: authUser.email,
        nombre: data.nombre,
        genero: data.genero,
      };
      await agregarUsuario(authUser.uid, userData);

      return userCredential;
    } catch (error) {
      // Manejar errores (ej. email ya en uso)
      console.error("Error al registrar:", error);
      throw error;
    }
  };

  const logout = () => {
    return signOut(auth);
  };

  // 5. Valor que proveerá el contexto
  const value = { user, loading, login, register, logout };

  // No renderizar nada hasta que sepamos si el usuario está logueado o no
  return (
    <AuthContext.Provider value={value}>
      {!loading && children}
    </AuthContext.Provider>
  );
};

// 6. Hook personalizado para consumir el contexto fácilmente
export const useAuth = () => {
  return useContext(AuthContext);
};
```

## Explicacion del AuthContext.js

1. Agregar importanciones necesarias
<img width="1560" height="130" alt="image" src="https://github.com/user-attachments/assets/12de90dd-7dfa-4617-bd9e-abab6257bb85" />

2. Crear Context, para implementar la logica de **`login`, `register` y `logout`**.
<img width="490" height="81" alt="image" src="https://github.com/user-attachments/assets/1c4b5ed7-e209-49ca-8987-0d9fe4532c9f" />

3. Crear el `AuthProvider` con la logica de autenticacion de la App. 
<img width="1359" height="880" alt="image" src="https://github.com/user-attachments/assets/8b19cfbe-7b3d-4f3e-ba8e-ca8bbb9d3ad9" />

4. En la function `register`, actualiza la logica de **datos a guardar en firestore** con los datos que solicitas en tu **Screen** de **Registro de Usuario**.
<img width="1217" height="706" alt="image" src="https://github.com/user-attachments/assets/d2e10a8f-c391-45be-9bd9-33154319480f" />

5. El Hook `useAuth`, te permite obtener el usuario autenticado y ejecutar las acciones **`login`, `register` y `logout`**.
<img width="839" height="133" alt="image" src="https://github.com/user-attachments/assets/0902f6aa-c85c-48e0-a16a-a14dec0c528e" />

