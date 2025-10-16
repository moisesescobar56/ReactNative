# Estructura de la App

**¿Por donde inicio el desarrollo de una app?**
1. **Documentacion y Analisis:** lo ideal es crear un prototipo y visualizar las pantallas a desarrollar con la calidad esperada.
2. **Diseño:** define el patron de diseño o la estructura de archivos utilizar.
3. **Desarrollo:**
   - **Frontend:** diseña las pantallas y la navegacion de la app.
   - **Backend:** implementa la integracion entre el frontend y la base de datos o [API Rest](https://youtube.com/shorts/_7CUdAEZir0?si=AxSZ5aOZE6k5AMWv) de tu aplicacion.
4. **Pruebas:** depura el funcionamiento de las pantallas en su [version alfa](https://es.wikipedia.org/wiki/Ciclo_de_vida_del_lanzamiento_de_software#Alfa) hasta que llegar al  0% de errores, cada error encontrado se debe depurar.
5. **Despligue:** has entrega de la [version beta](https://es.wikipedia.org/wiki/Ciclo_de_vida_del_lanzamiento_de_software#Beta) de la app a los usuarios finales.
6. **Implementacion:** entrega la [version final (RC)](https://es.wikipedia.org/wiki/Ciclo_de_vida_del_lanzamiento_de_software#Versi%C3%B3n_candidata_a_definitiva_(RC)) al cliente/product owner.

<img width="414" height="146" alt="image" src="https://github.com/user-attachments/assets/a3551759-96c0-48b0-a4c9-907cbb011387" />

[Leer más](https://support.google.com/a/answer/11202276?hl=es)

## Estructura de archivos App

**Indicacion:** crea las siguientes carpetas y archivos en tu proyecto.

> [!NOTE]
> En la carpeta `📁screens` crea las pantallas de tu proyecto.

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

**NPM:**
```code
npx create-expo-app@latest AppNoticias --template blank
cd AppNoticias
npx expo install react-dom react-native-web
code .
```

**Resultado**
<img width="1711" height="900" alt="image" src="https://github.com/user-attachments/assets/04c6014c-c0f9-4714-b942-874bf50ffc3e" />

# Crear componentes
  
**Indicacion:** crea y diseña los componentes que usaras en tu app. Puedes usar los componentes por defecto o usar los componentes personalizados a continuacion:

📁 components
- index.js 
- Layout.js
- Input.js
- ButtonRounded.js

**Layout.js**
```js
import { StyleSheet, StatusBar, View } from "react-native";
import { SafeAreaView, SafeAreaProvider } from "react-native-safe-area-context";

export default function Layout({ children }) {
  return (
    <SafeAreaProvider>
      <SafeAreaView style={styles.container} >
        <StatusBar barStyle="light-content" backgroundColor="#0051caff" />
        <View style={styles.body} >
            {children}
        </View>
      </SafeAreaView>
    </SafeAreaProvider>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1, // Ocupa todo el espacio.
    backgroundColor: "#f5f5f5", // Fondo gris claro.
    justifyContent: "center", // Centra el contenido verticalmente.
    alignItems: "stretch", // estira el contenido horizontalmente.
  },
  body: {
    flex: 1, // Ocupa el espacio restante.
    justifyContent: "top", // Alinea el contenido arriba.
    alignItems: "left", // Alinea el contenido a la izquierda.
    padding: 5, // Agrega un relleno de 5px.
  },
});
```

**Input.js**
```js
import { TextInput, Text, View, StyleSheet } from "react-native";

export default function Input({ label, placeholder, type = "default", editable = true, lines = 1, value = "", onChangeText }){
    return (
        <View style={styles.container} >
            <Text style={styles.label} >{label}</Text>
            <TextInput 
                placeholder={placeholder}
                keyboardType= {type}
                editable = {editable}
                style={ lines > 1? styles.textArea : styles.control }
                placeholderTextColor="#999"
                multiline={ lines > 1? true : false }
                numberOfLines= {lines}
                textAlignVertical="top"
                value={value}
                onChangeText={onChangeText}
             />
        </View>
    );
}

const styles = StyleSheet.create({
    container:{
        width: "auto", 
        paddingHorizontal: 5,
        paddingBottom: 5,
        marginBottom: 5,
    },
    label:{
        fontSize: 14,
        fontWeight: "bold",
        color: "#000",
        marginBottom: 5
    },
    control:{
        width: "100%",
        fontSize: 16,
        height: 45,
        borderColor: "#999",
        borderStyle: "solid",
        borderWidth: 1,
        padding: 10
    },
    textArea:{
        width: "100%",
        fontSize: 16,
        height: 120,
        borderColor: "#999",
        borderStyle: "solid",
        borderWidth: 1,
        padding: 10,
        justifyContent: "flex-start"
    }
});
```

**ButtonRounded.js**
```js
import { TouchableOpacity, Text, StyleSheet } from "react-native";

export default function ButtonRounded({ title, onPress, isPrimary = true }) {
  return (
    <TouchableOpacity
      onPress={onPress}
      activeOpacity={0.8}
      style={[ styles.button, isPrimary ? styles.primary : styles.secondary, ]} >
      <Text
        style={[ styles.text, isPrimary ? styles.textPrimary : styles.textSecondary, ]} >
        {title}
      </Text>
    </TouchableOpacity>
  );
}

const styles = StyleSheet.create({
  button: {
    paddingVertical: 12,
    paddingHorizontal: 20,
    borderRadius: 25,
    alignItems: "center",
    justifyContent: "center",
    marginVertical: 8,
    elevation: 3,
    shadowColor: "#000",
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.2,
    shadowRadius: 3,
  },
  primary: {
    backgroundColor: "#2563EB", // azul
  },
  secondary: {
    backgroundColor: "#FFF",
    borderWidth: 1.5,
    borderColor: "#2563EB",
  },
  text: {
    fontSize: 16,
    fontWeight: "600",
  },
  textPrimary: {
    color: "#FFF",
  },
  textSecondary: {
    color: "#2563EB",
  },
});
```


