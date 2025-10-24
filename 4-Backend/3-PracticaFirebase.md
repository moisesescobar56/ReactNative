# App Noticias (Mostrar y registro)

## Clonar proyecto

**PASO 1:** copia y clona en VS Code el proyecto.
```code
https://github.com/moisesescobar56/AppNoticiasV2.git
```

**PASO 2:** al finalizar,abre una terminal e instala los paquetes mediante `npm`.
```code
npm install
```

<img width="1804" height="703" alt="image" src="https://github.com/user-attachments/assets/d2970a93-2146-41d8-8598-737ef6eae390" />


## Configurar Firebase.js

**PASO 1:** crea una app en firebase y copia la configuracion en el archivo **`📁api/firebase.js`**.

<img width="1804" height="847" alt="image" src="https://github.com/user-attachments/assets/6a25cd7e-6d46-4a6b-943c-8ab1b1dd33fb" />

**PASO 2:** agrega las importaciones y exportaciones de los servicios al archivo `📁api/firebase.js`.

**Importaciones**
```js
import { getAuth } from "firebase/auth"; 
import { getFirestore } from "firebase/firestore";
import { getStorage } from "firebase/storage";
```

**Exportaciones**
```js
// Inicializar y exportar servicios
export const auth = getAuth(app);  // autenticar
export const db = getFirestore(app); // base de datos
export const storage = getStorage(app); // archivos
export { app };
```

<img width="1807" height="851" alt="image" src="https://github.com/user-attachments/assets/015467c2-a4db-45d2-be2e-42217558fd50" />

## Crear servicio

**PASO 1:** en la carpeta `📁 services`, crea un nuevo servicio con el nombre de tu coleccion.

```code
newService.js
```

**PASO 2:** agrega las importaciones necesarias en el **newService.js**.
```js
import { db } from "../api/firebase";
import { collection, getDocs, addDoc, doc, query,orderBy, where } from "firebase/firestore";
// referencia a la collection
const noticiasRef = collection(db, "noticias");
```

<img width="1807" height="851" alt="image" src="https://github.com/user-attachments/assets/d6d5eafb-f676-4716-bceb-9baaa67c5a15" />

**PASO 3:** agregar las `function` para realizar las peticiones que se haran a la `collection`.
```js
export async function obtenerNoticias() {
  try {
    let q = query(noticiasRef, orderBy("fechaHora", "desc"));

    const snap = await getDocs(q);
    const array = snap.docs.map(d => ({  id: d.id, ...d.data() }));
    return array;

  } catch (err) {
    console.error("Error obtenerNoticias:", err);
  }
}

export async function agregarNoticia({ titulo, contenido, imagenUrl }) {
      const noticia = {
        titulo: titulo.trim(),
        fechaHora: new Date(),
        imagenUrl: imagenUrl.trim(),
        contenido: contenido.trim(),
      };
      await addDoc(noticiasRef, noticia);
}
```

<img width="1807" height="952" alt="image" src="https://github.com/user-attachments/assets/2ca22e56-1eb6-4150-ad6c-35118ea89340" />

**PASO 4:** agrega `utils  functions` para tratar los datos de tu collection.
```js
export function formatDate(d) {
  // formatear fecha
  const date = new Date(d.seconds * 1000);
  return date.toLocaleDateString("es-SV", {
    year: "numeric",
    month: "long",
    day: "numeric",
  });
}
```
<img width="1807" height="952" alt="image" src="https://github.com/user-attachments/assets/b297df2c-82bb-4738-928c-e2b50762a54e" />

## Usar ObtenerNoticias en NewScreen.js

**PASO 1:** agrega las importaciones necesarias para codificar la logica.
```js
import { FlatList, Text, Image, TouchableOpacity, ActivityIndicator, StyleSheet  } from 'react-native';
import { obtenerNoticias, formatDate } from '../services/newService';
```

<img width="1896" height="812" alt="image" src="https://github.com/user-attachments/assets/f02bde9d-2dcc-4253-900a-7be5db1e26b4" />


**PASO 2:** crea las `variables` que usaras en la screen.
```js
const [loading, setLoading] = useState(true);
    const [datos, setDatos] = useState([]);
```
<img width="1896" height="812" alt="image" src="https://github.com/user-attachments/assets/b1905abe-ebfb-484a-b8b5-9c33857c0b38" />

**PASO 3:** crea una function **asincrona** para `obtener` los datos de firebase.
```js
async function buscar() {
    try {
        const lista = await obtenerNoticias();
        setDatos(lista); // cargar noticias
    } catch (error) {
        console.error(error);
    } finally {
        setLoading(false);
    }
}
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/94b8b840-d8f2-4b82-bee9-c8b85caf7c12" />


**PASO 4:** crea un `useEffect` para actualizar la `screen` cuando se actualicen los datos.
```js
useEffect(() => {
    buscar();
},[datos]);
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/199b6d0b-95c1-4179-ba9a-076cdd422cc1" />


**PASO 5:** crea una function de `render`, para crear la informacion en la screen.

```js
function renderItem({ item }){
    return (
        <TouchableOpacity style={styles.card} onPress={() => navigation.navigate('ViewNew', { noticia: item })} >
            <Image style={styles.image} source={{uri: item.imagenUrl}} />
            <Text style={styles.title}>{item.titulo}</Text>
            <Text style={styles.date}>{formatDate(item.fechaHora)}</Text>
        </TouchableOpacity>
    );
}
```
<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/9f01b2b6-052e-4d42-ab96-f1e45834ae75" />

**PASO 6:** implementa un `ActivityIndicator` para mostrar al usuario que algo esta pasando, es decir estan cargando los datos.
```js
if (loading) return <ActivityIndicator style={{ flex: 1 }} />;
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/0c838323-eb94-4861-bf22-47bd8d78843e" />


**PASO 7:** agrega un `` para renderizar la informacion obtenida de firebase.

```js
<FlatList
    data={datos}
    renderItem={renderItem}
    keyExtractor={(x) => x.id}
/>
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/59d111ac-6bdc-4b45-adc0-9aa5809ffd43" />


## Usar agregarNoticia en RegisterNewScreen.js

**PASO 1:** agrega las importaciones necesarias para codificar la logica.

```js
import { agregarNoticia } from '../services/newService';
import { Alert } from 'react-native';
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/7b485c5b-b0fd-46a4-8b5d-c75fa336aa5d" />


**PASO 2:** crea las `variables` que usaras en la screen.
```js
const [titulo, setTitulo] = useState('');
const [imagenUrl, setImagenUrl] = useState('');
const [contenido, setContenido] = useState('');
```
<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/80ba3e8d-f4d4-4771-8de9-ef9710394b84" />

**PASO 3:** crea una function **asincrona** para `guardar` los datos de firebase.
```js
    async function guardar(){
        //validar
        if (!titulo || !imagenUrl || !contenido) {
          Alert.alert( "Error", "Por favor, completa todos los campos obligatorios." );
          return;
        }

        // guardar noticia
        await agregarNoticia({
            titulo: titulo,
            imagenUrl: imagenUrl,
            contenido: contenido
        });

        navigation.popToTop(); //cerrar screen
    }
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/18417f26-8ba9-488d-90e4-8a8b8ab92017" />

**PASO 4:** implementa la `function` en la propiedad `onPress` del button.
```js
<ButtonRounded title="Guardar" onPress={guardar} />
```
<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/1e748b80-6bb7-4f24-a090-3cdbc857e531" />

## Testing
Al finalizar, inicia la app y realiza las pruebas de la integracion de firebase.

<img width="1140" height="737" alt="image" src="https://github.com/user-attachments/assets/bc6a2b7b-6398-4f64-a969-42d56d402c2d" />
