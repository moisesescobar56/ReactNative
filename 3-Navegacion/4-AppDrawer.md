# Navegacion con Drawer

## Instalar React Navigation [Stack] y [Drawer]

**PASO 1:** Instalar el paquete npm React Navigation [Stack] y [Drawer]
```code
npm install @react-navigation/stack
npm install @react-navigation/drawer
```

**PASO 2:** Instalar el paquete npm de gestos.
```code
npx expo install react-native-gesture-handler react-native-reanimated react-native-worklets
```

**PASO 3:** editar el archivo **`📁nagivation > AppDrawer.js`**.
```js
import { createDrawerNavigator } from '@react-navigation/drawer';

// importar screens del menu lateral
import LoginScreen from '../screens/LoginScreen';
import RegisterScreen from  '../screens/RegisterScreen';

// crear menu lateral
const Drawer = createDrawerNavigator();

// exportar menu lateral
export default function AppDrawer() {
  return (
    <Drawer.Navigator>
      <Drawer.Screen name="Login" component={LoginScreen} options={{ title: "Iniciar sesión" }} />
      <Drawer.Screen name="Register" component={RegisterScreen} options={{ title: "Registrarse" }} />
    </Drawer.Navigator>
  );
}
```

<img width="1742" height="906" alt="image" src="https://github.com/user-attachments/assets/7e2c961e-c54a-4656-961e-4f78380027f0" />

**PASO 4:** editar el archivo **`App.js`**.
```js
// importar menu lateral
import AppDrawer from './navigation/AppDrawer';

// importar screens que no se usan en el menu lateral
import NewScreen from './screens/NewScreen';
import ViewNewScreen from './screens/ViewNewScreen';

// importar react navigation
import { createStackNavigator } from '@react-navigation/stack';
import { NavigationContainer } from '@react-navigation/native';

// crear Stack
const Stack = createStackNavigator();

// exportar App
export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Home" component={AppDrawer} options={{ headerShown: false }} />
        <Stack.Screen name="New" component={NewScreen} options={{ title: "Noticias" }}  />
        <Stack.Screen name="ViewNew" component={ViewNewScreen} options={{ title: "Ver Noticia" }}  />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

<img width="1742" height="971" alt="image" src="https://github.com/user-attachments/assets/75b4efc4-1086-4817-b68e-c9fc293eb111" />

**PASO 5:** iniciar la app y verifica que funcione el menu lateral.

### Menu lateral > LoginScreen 
<img width="941" height="809" alt="image" src="https://github.com/user-attachments/assets/e6e516db-0b95-4d17-8da9-7d15b15e556b" />

### Menu lateral > RegisterScreen 
<img width="941" height="814" alt="image" src="https://github.com/user-attachments/assets/35ffe1eb-0ac6-461e-bb40-c916c6839393" />

## Implementar iconos

**PASO 1:** instalar `vector-icons`.
```code
npm install react-native-vector-icons
```

**PASO 2:** importar `vector-icons` en el archivo **`📁nagivation > AppDrawer.js`**.
```js
import { Ionicons } from '@expo/vector-icons';
```

<img width="1742" height="935" alt="image" src="https://github.com/user-attachments/assets/f2bd5581-8464-4c53-b460-5b857280bd0f" />


**PASO 3:** editar en el archivo cada `<Drawer.Screen>`.

**EJEMPLO:**
```js
<Drawer.Screen name="Home" component={HomeScreen} 
  options={{ 
    title: "Inicio", 
    drawerIcon: ({ color, size }) => <Ionicons name="home-outline" size={size} color={color} />,
  }} />
```

<img width="1786" height="991" alt="image" src="https://github.com/user-attachments/assets/68f1eb9b-9213-48dd-9858-b8fa8b1a1a75" />

**PASO 4:** iniciar la app y verifica que funcione el menu lateral.

### Menu lateral > LoginScreen 
<img width="941" height="813" alt="image" src="https://github.com/user-attachments/assets/1ffe52b0-3316-4f27-bb92-60ee5b35a77d" />

### Menu lateral > RegisterScreen 
<img width="941" height="815" alt="image" src="https://github.com/user-attachments/assets/5ce7f860-80f7-404d-8c27-6a2c80ab832c" />
