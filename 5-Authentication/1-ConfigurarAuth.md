# Configurar Auth Firebase

## Inicializar el servicio Authentication

**PASO 1:** en el proyecto de Firebase accede a **Compilacion > Authentication**.

<img width="1606" height="859" alt="image" src="https://github.com/user-attachments/assets/ceeeb914-7e33-468e-ab95-15570451999f" />

**PASO 2:** haz clic en **Comenzar**.

<img width="1606" height="859" alt="image" src="https://github.com/user-attachments/assets/7655632f-1602-4ba9-aaa2-593b63f81ffc" />

**PASO 3:** selecciona el metodo de acceso por `Correo electronico/contraseña`.

<img width="1730" height="859" alt="image" src="https://github.com/user-attachments/assets/2cebf1d7-30df-4628-bb66-61931a570623" />

**PASO 4:** habilita el servicio y haz clic en **Guardar**.

<img width="1730" height="859" alt="image" src="https://github.com/user-attachments/assets/a5d19bec-6c0b-443b-9762-d4b75e64c161" />

**Resultado:**

<img width="1730" height="859" alt="image" src="https://github.com/user-attachments/assets/424aa0cf-5385-463c-9fbf-41c9beef5e88" />


## Comprobar configuracion en `📁api/firebase.js`

**NOTA:** verifica que se hayan inicializado los servicios de `getAuth` y `getFirestore` para poder consumirlos.

<img width="1511" height="949" alt="image" src="https://github.com/user-attachments/assets/c27a65d7-d122-4b45-961d-95905796f8a6" />

## Crear base de datos Firestore

**NOTA:** si ya tienes una **base de datos de `firestore`** y **collection de `usuarios`**, puedes omitir estos pasos.

**PASO 1:** accede en el panel lateral a **Authentication** y haz clic en **Comenzar**.
<img width="1730" height="859" alt="image" src="https://github.com/user-attachments/assets/9ed5761b-2f1e-4ccf-8b78-3ddcee1e9cfe" />

**PASO 2:** seleccionar la edicion **Estandar** y haz clic en **Siguiente**.

<img width="1730" height="859" alt="image" src="https://github.com/user-attachments/assets/7e12acf1-309a-45ed-be3a-e2bcf826c7ef" />

**PASO 3:** haz clic en **Siguiente**.
<img width="1730" height="859" alt="image" src="https://github.com/user-attachments/assets/7d6b696a-b453-4995-8592-6a3e9bfcd6b2" />

**PASO 4:** selecciona **Comenzar en `Modo prueba`** y haz clic en **Crear**.

<img width="1730" height="976" alt="image" src="https://github.com/user-attachments/assets/b8990688-95e9-4cde-b6ba-530ee03e9122" />

**Resultado:**

<img width="1924" height="1024" alt="image" src="https://github.com/user-attachments/assets/1ce72287-b02b-4034-9a6f-d422055ef62a" />
