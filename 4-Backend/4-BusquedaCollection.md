# App Noticias (buscar por titulo)

## Crear component `SearchBar`

**PASO 1:** crear un nuevo componente llamada  `SearchBar.js` en la carpeta **📁components**.
```code
SearchBar.js
```

<img width="1507" height="800" alt="image" src="https://github.com/user-attachments/assets/ff63cfe6-4289-4acc-ac33-8f8f93601703" />


**PASO 2:** agregar las referencias, estructura y estilos del componente.

```js
import { View, TextInput,  StyleSheet,} from "react-native";
import { Ionicons } from "@expo/vector-icons"; // Usamos Ionicons para el icono

export default function SearchBar({ text, setText, onSearch }) {
  return (
    <View style={styles.container}>
      <View style={styles.inputWrapper}>
        <Ionicons name="search" size={20} color="#888" style={styles.icon} />
        <TextInput
          style={styles.input}
          placeholder="Buscar..."
          value={text}
          onChangeText={setText}
          returnKeyType="search"
          onSubmitEditing={onSearch}
        />
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
    container: {
        flexDirection: "row",
        alignItems: "center",
        paddingTop: 10,
        paddingBottom: 10,
    },
    inputWrapper: {
        flex: 1,
        flexDirection: "row",
        alignItems: "center",
        backgroundColor: "#fff",
        borderRadius: 6,
        borderColor: "#ddd",
        marginRight: 10,
        height: 40,
    },
    input: {
        flex: 1,
        height: "100%",
        fontSize: 16,
    },
    icon: {
        paddingLeft: 10, 
        paddingRight: 5,
    },
});
```

<img width="1641" height="960" alt="image" src="https://github.com/user-attachments/assets/a7386b26-5540-4734-98c0-9500f2aed3a0" />


**PASO 3:** agregar exportacion de componente en el archivo **📁components/index.js**.
```js
export { default as SearchBar } from './SearchBar';
```
<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/5263dac2-e678-43c3-88ec-462d218372b0" />


## Actualizar la function `obtenerNoticias` en newService.js

**PASO 1:** abrir el archivo newService.js y en la function `obtenerNoticias` agregar un parametro de `titulo`.

<img width="1645" height="1027" alt="image" src="https://github.com/user-attachments/assets/c152814c-491b-4d85-9fb6-7675c5b8491e" />


**PASO 2:** agregar la logica para hacer una consulta por titulo a firestore.
```js
if (titulo) {
  const startAt = titulo;
  const endAt = titulo + '\uf8ff';
  q = query(
    noticiasRef,
    where("titulo", ">=", startAt),
    where("titulo", "<=", endAt),
    orderBy("titulo", "asc"),
  );
}
```

<img width="1645" height="1027" alt="image" src="https://github.com/user-attachments/assets/10def7e2-24a2-4ee2-90cf-71b7f400e84b" />

## Implementar la `SearchBar` y realizar busquedas.

**PASO 1:** agregar el componente `SearchBar` en las dependecias.

<img width="1645" height="1027" alt="image" src="https://github.com/user-attachments/assets/6c211af1-f72a-4d49-ba71-1bfba113686f" />


**PASO 2:** declarar la variable `titulo` y pasarla a la function `obtenerNoticias`.
```js
const [titulo, setTitulo] = useState('');
```

<img width="1645" height="1027" alt="image" src="https://github.com/user-attachments/assets/817585a9-f396-407e-8a17-fcd48e388f7e" />


**PASO 3:** agregar el `SearchBar` al elemento **FlatList** para realizar la busqueda.
```js
ListHeaderComponent={ <SearchBar text={titulo} setText={setTitulo} onSearch={ buscar } /> }
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/89215c4b-1c0a-4dc0-b12e-f64947f05463" />


**PASO 4:** iniciar la app en **Expo Go** y realizar pruebas.

<img width="742" height="737" alt="image" src="https://github.com/user-attachments/assets/94e29a77-97af-4c3f-9520-2302e44b1477" />
