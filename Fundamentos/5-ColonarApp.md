# Clonar App desde repositorio GitHub

## Requisitos
- Git x64 instalado.
- Cuenta de GitHub.
- Conocimientos basicos de Git.
- Haber recibido una invitacion para colaborar en el repositorio.

## Agregar miembros al repositorio (Propietario del repositorio)

> [!IMPORTANT]
> Estos pasos los debe realizar el propietario del repositorio.  

**PASO 1:** ir desde el repositorio a **Settings**.

<img width="1288" height="886" alt="image" src="https://github.com/user-attachments/assets/4d9b832e-91bb-4ae7-9b05-4fc5b627e762" />

**PASO 2:** seleccionar **Collaborators**.

<img width="1288" height="886" alt="image" src="https://github.com/user-attachments/assets/649158a2-0323-4988-b1e5-2af1743dcc23" />

**PASO 3:** seleccionar **Add people** para invitar los miembros del equipo.

<img width="1445" height="1057" alt="image" src="https://github.com/user-attachments/assets/5a76faed-0073-4306-bf73-fd49bd46e218" />

**PASO 4:** escribir el nombre de usuario o email del los miembros (solo permite uno a la vez). 

<img width="1445" height="1057" alt="image" src="https://github.com/user-attachments/assets/6c9c37de-666d-479d-a35e-ac7969fba0ab" />

**PASO 5:** dar clic en **Add** para enviar la invitacion al repositorio.

<img width="1445" height="1057" alt="image" src="https://github.com/user-attachments/assets/965eb90d-b7fe-471f-bc40-44e328a42261" />

**Resultado:** el usuario invitado debe revisar su bandeja de entrada del email.

<img width="1445" height="1057" alt="image" src="https://github.com/user-attachments/assets/2803ce3b-30c8-4976-9c84-aef1f777f926" />

**NOTA:** repetir los paso 3,4 y 5 por cada integrante.

## Aceptar invitacion para colaborar (Invitado)

> [!IMPORTANT]
> Estos pasos los debe realizar el invitado al repositorio.  

**PASO 1:** buscar el correo donde indique que has sido invitado al repositorio correspondiente. Dar clic en **View invitation**.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9b3807da-c8dc-4f8f-8ce8-cf04e2f18e54" />

**PASO 2:** dar clic en **Aceptar** la invitacion (iniciar sesion para poder aceptar la solicitud). 

<img width="1462" height="927" alt="image" src="https://github.com/user-attachments/assets/e55d5256-6d73-416e-8d93-1c5d7e79fc9d" />

**RESULTADO:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/495c5b31-6664-4aac-b87c-71ee2dc3a653" />

## Clonar repositorio 

**PASO 1:** acceder al repositorio, seleccionar la opcion **Code > Copiar enlace HTTPS**.

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4bb343ce-5f07-40f5-a5de-1248b0fef652" />

**PASO 2:** abrir VS Code en blanco, sin ningun proyecto abierto.

> [!NOTE]
> Para cerrar un proyecto en VS Code puedes seleccionar **File > Close Folder**.

<img width="1600" height="838" alt="image" src="https://github.com/user-attachments/assets/f9639c14-39cd-42c2-90b8-3971122a4a07" />

**PASO 3:** seleccionar la opcion **Clone Repository**.

<img width="1600" height="838" alt="image" src="https://github.com/user-attachments/assets/73e1322c-6165-43d9-8c15-bdb87794105c" />

**PASO 4:** pegar la **url del repositorio** copiada anteriormente y presionar **Enter**.

<img width="1600" height="838" alt="image" src="https://github.com/user-attachments/assets/42f87b0d-b068-4db6-9587-a2e7622de745" />

**PASO 5:** seleccionar la carpeta donde y da clic en **Select as Repository Destination**.

<img width="1597" height="837" alt="image" src="https://github.com/user-attachments/assets/5fd4d1bd-e60c-4aa3-a05a-14788eb2fccb" />

**PASO 6:** al finalizar la descarga, da clic en **Open** para abrir el repositorio clonado.

<img width="1594" height="836" alt="image" src="https://github.com/user-attachments/assets/899c3533-2982-4a90-a0af-816186275f34" />

**PASO 7:** dar clic en **"Yes, I trust the authors"**.

<img width="1600" height="838" alt="image" src="https://github.com/user-attachments/assets/5150844f-fbdc-4d9b-9817-7c27d79f064c" />

**Resultado:**

> [!WARNING]
> Al clonar un repositorio de un proyecto Node.js, no viene la carpeta **node_modules**, debes instalar los paquetes **`npm`** requeridos.

<img width="1600" height="839" alt="image" src="https://github.com/user-attachments/assets/ca02c5ba-118d-489e-8d36-ff1ba2336baf" />

## Instalar paquetes `NPM` en proyecto Node.js

**PASO 1:** abrir una **`terminal`** en VS Code.

<img width="1600" height="838" alt="image" src="https://github.com/user-attachments/assets/eef2af52-e42c-47ab-afca-6e8ea939de44" />

**PASO 2:** escribir el comando **`npm install`** y presionar **Enter**.

```code
npm install
```

<img width="1600" height="838" alt="image" src="https://github.com/user-attachments/assets/8b409e81-f912-41fc-96f3-55dffb18c1f1" />

**Resultado:** ahora ya tienes listo tu repositorio clonado.
<img width="1600" height="838" alt="image" src="https://github.com/user-attachments/assets/904b96a3-a60a-44a2-8786-895fc30c0916" />


