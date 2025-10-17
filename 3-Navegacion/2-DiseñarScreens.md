# Diseño de pantallas de la App

**¿Por donde inicio el desarrollo de una app?**
1. **Documentacion y Analisis:** lo ideal es crear un prototipo y visualizar las pantallas a desarrollar con la calidad esperada.
2. **Diseño:** define el patron de diseño o la estructura de archivos utilizar.
3. **Desarrollo:**
   - **Frontend:** diseña las pantallas y la navegacion de la app.
   - **Backend:** implementa la integracion entre el frontend y la base de datos o [API Rest](https://youtube.com/shorts/_7CUdAEZir0?si=AxSZ5aOZE6k5AMWv) de tu aplicacion.
4. **Pruebas:** depura el funcionamiento de las pantallas en su [version alfa](https://es.wikipedia.org/wiki/Ciclo_de_vida_del_lanzamiento_de_software#Alfa) hasta que llegar al  0% de errores, cada error encontrado se debe depurar.
5. **Despligue:** has entrega de la [version beta](https://es.wikipedia.org/wiki/Ciclo_de_vida_del_lanzamiento_de_software#Beta) de la app a los usuarios finales.
6. **Implementacion:** entrega la [version final (RC)](https://es.wikipedia.org/wiki/Ciclo_de_vida_del_lanzamiento_de_software#Versi%C3%B3n_candidata_a_definitiva_(RC)) al cliente/product owner.

<img width="1284" height="724" alt="image" src="https://github.com/user-attachments/assets/0b7bc00f-6ec4-4025-b521-075c04ebdc31" />

## Diseño de pantallas

**Indicacion:** diseña las pantallas de tu proyecto.

> [!NOTE]
> En la carpeta `📁screens` estan las pantallas de tu proyecto.

📁 api\
📁 components
- index.js 
- Layout.js
- Input.js
- ButtonRounded.js

📁 navigation
- AppDrawer.js
- AppTabs.js

📁 screens
- LoginScreen.js
- RegisterScreen.js
- NewsScreen.js
- ViewNewScreen.js

📁 services


**Estructura**
<img width="1711" height="900" alt="image" src="https://github.com/user-attachments/assets/04c6014c-c0f9-4714-b942-874bf50ffc3e" />

# Diseñar Screens
  
**Indicacion:** crea y diseña las screens que usaras en tu app.

📁 screens
- LoginScreen.js
- RegisterScreen.js
- NewsScreen.js
- ViewNewScreen.js

**LoginScreen.js**
```js
import { useState, useEffect } from 'react';
import { Layout, Input, ButtonRounded } from '../components';

export default function LoginScreen(){
    const [email, setEmail] = useState('');
    const [clave, setClave] = useState('');

    return (
        <Layout>
            <Input 
                label="Correo electronico"
                placeholder="codigo@esfe.agape.edu.sv"
                type="email-address"
                value={email}
                onChangeText={setEmail} />
            <Input 
                label="Constraseña"
                placeholder="*****"
                hideText={true}
                value={clave}
                onChangeText={setClave} />
            <ButtonRounded title="Entrar" />    
            <ButtonRounded title="Registrarse" isPrimary={false} />    
        </Layout>
    );
}
```
> [!TIP]
> Crea las variables cuando diseñes las pantallas que tienen `<Input />`. En este caso `email` y `clave`.

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/a66dfe4d-54e0-42e3-b7ec-4629b9bcc545" />


**Resultado:**

<img width="459" height="814" alt="image" src="https://github.com/user-attachments/assets/69f147f6-4b93-422c-aeb7-6952d29c18f7" />

**RegisterScreen.js**
```js
import { useState, useEffect } from 'react';
import { Layout, Input, ButtonRounded } from '../components';

export default function RegisterScreen(){
    const [nombre, setNombre] = useState('');
    const [genero, setGenero] = useState('');
    const [email, setEmail] = useState('');
    const [clave, setClave] = useState('');
    const [confirmarClave, setConfirmarClave] = useState('');

    return (
        <Layout>
            <Input 
                label="Nombre"
                placeholder="Juan Perez"
                type="default"
                value={nombre}
                onChangeText={setNombre} />
            <Input 
                label="Genero"
                placeholder="Femenino/Masculino"
                type="default"
                value={genero}
                onChangeText={setGenero} />                  
            <Input 
                label="Correo electronico"
                placeholder="codigo@esfe.agape.edu.sv"
                type="email-address"
                value={email}
                onChangeText={setEmail} />
            <Input 
                label="Constraseña"
                placeholder="*****"
                hideText={true}
                value={clave}
                onChangeText={setClave} />
            <Input 
                label="Confirmar constraseña"
                placeholder="*****"
                hideText={true}
                value={confirmarClave}
                onChangeText={setConfirmarClave} />
            <ButtonRounded title="Confirmar" />    
            <ButtonRounded title="Iniciar sesion" isPrimary={false} />    
        </Layout>
    );
}
```
> [!TIP]
> Crea las variables cuando diseñes las pantallas que tienen `<Input />`. En este caso `nombre`, `genero`, `email`, `clave` y `confirmarClave`.

<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/fbe93582-18d2-46bb-9bfc-07e186cc6209" />

**Resultado:**

<img width="454" height="811" alt="image" src="https://github.com/user-attachments/assets/9449d83a-92f5-43b3-a1b2-8aae08440e47" />

**NewScreen.js**
```js
import { useState, useEffect } from 'react';
import { Layout, Input, ButtonRounded } from '../components';

export default function NewScreen(){
    const [titulo, setTitulo] = useState('');

    return (
        <Layout>
            <Input 
                label="Buscar"
                placeholder="escribir aqui..."
                type="default"
                value={titulo}
                onChangeText={setTitulo} />

        </Layout>
    );
}
```
> [!TIP]
> Crea las variables cuando diseñes las pantallas que tienen `<Input />`. En este caso `nombre`, `genero`, `email`, `clave` y `confirmarClave`.

<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/9151a8da-20b2-4590-9403-c2376f27d643" />

**Resultado:**
<img width="454" height="811" alt="image" src="https://github.com/user-attachments/assets/821006ca-d083-4a92-b305-b4b0cc8c8280" />

**ViewNewScreen.js**
```js
import { useState, useEffect } from 'react';
import { Layout, Input, ButtonRounded } from '../components';

export default function ViewNewScreen(){

    return (
        <Layout>

        </Layout>
    );
}
```

> [!TIP]
> Crea las variables cuando diseñes las pantallas que tienen `<Input />`. En este caso no hay ninguna.
<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/3d459aea-b4b6-457a-888c-e8f521a8afb3" />

**Resultado:**

<img width="463" height="815" alt="image" src="https://github.com/user-attachments/assets/d854a4f0-c3b8-4e12-8ae8-a828a9ab4e44" />
