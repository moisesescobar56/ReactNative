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

