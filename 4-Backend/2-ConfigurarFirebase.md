# Configurar Firebase en App

## Crear App en Firebase
**PASO 1:** dar clic en **Agregar App**.

<img width="1663" height="589" alt="image" src="https://github.com/user-attachments/assets/3ae5d7a5-2709-4f78-ab67-3b67f1bdc02a" />

**PASO 2:** seleccionar **Web**.

<img width="1663" height="579" alt="image" src="https://github.com/user-attachments/assets/26e39274-d60f-435c-933d-6db0d01075e5" />

**PASO 3:** asgina un nombre a la App, diferencialo del proyecto agregando la version y da clic en **Registrar App**.
```code
AppNombreV1
```
<img width="1666" height="951" alt="image" src="https://github.com/user-attachments/assets/b7ecae40-99fd-4709-960f-5607e4143ea3" />

**PASO 4:** copia la configuracion de tu App, guardalos en un archivo de forma temporal.

<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/b698b2af-6eb7-4772-a34f-7848a9a2cf43" />

## Crear archivo firebase.js en App

**PASO 1:** en la carpeta `📁api` de tu proyecto, crea un nuevo archivo llamado **`firebase.js`**.

<img width="1507" height="871" alt="image" src="https://github.com/user-attachments/assets/90026081-3e12-4b44-83fd-76207048a53b" />

**PASO 2:** pega la configuracion copiada al crear tu `App` en firebase console y elimina los comentarios innecesarios.

<img width="1507" height="871" alt="image" src="https://github.com/user-attachments/assets/e2e0ad43-34c4-4fcf-abbf-39365a422e53" />

**Resultado:**

<img width="1504" height="768" alt="image" src="https://github.com/user-attachments/assets/dbbbcb80-23da-4c3b-aff2-527a1e086171" />

**PASO 3:** importa las dependecias a otros servicios de Firebase que puedes usar, como `Firestore`, `Authentication` y `Storage`.
```js
import { getAuth } from "firebase/auth"; 
import { getFirestore } from "firebase/firestore";
import { getStorage } from "firebase/storage";
```
<img width="1507" height="771" alt="image" src="https://github.com/user-attachments/assets/24f5d1e4-4e11-4e64-aef0-aa9222d27f21" />


**PASO 4:** inicializa y exporta los servicios de  `Firestore`, `Authentication` y `Storage`.
```js
// Inicializar y exportar servicios
export const auth = getAuth(app);  // autenticar
export const db = getFirestore(app); // base de datos
export const storage = getStorage(app); // archivos
export { app };
```

<img width="1507" height="876" alt="image" src="https://github.com/user-attachments/assets/afa721b7-aecc-4be3-96cc-91c84693700e" />

**PASO 5:** abre una terminal e instala `firebase` en tu proyecto de expo react native.

```code
npx expo install firebase
```
<img width="1507" height="876" alt="image" src="https://github.com/user-attachments/assets/09a98d26-f211-4677-b066-e690a977a0a5" />

**Resultado:**
<img width="1507" height="876" alt="image" src="https://github.com/user-attachments/assets/8f4e5cc5-776f-421d-bfc1-16355cc0963d" />



