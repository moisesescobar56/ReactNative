# Configuracion de navegacion para usuarios autenticados

**Qué es un AppNavigator**
En aplicaciones React Native que usan React Navigation, un navigator es básicamente un componente que define cómo se mueven los usuarios entre pantallas.
- Puede ser un StackNavigator (pila de pantallas, una encima de otra)
- Puede ser un TabNavigator (pestañas inferiores)
- Puede ser un DrawerNavigator (menú lateral)

Un `AppNavigator` es simplemente un componente que agrupa y organiza todos los navigators de la app, combinando stacks, tabs y drawers según la lógica de navegación que quieras.

## Configurar AppNavigator

**PASO 1:** crea un archivo llamdo `AppNavigator.js` en la carpeta **`📁navigation`**.

```code
AppNavigator.js
```
<img width="1511" height="751" alt="image" src="https://github.com/user-attachments/assets/456867f9-df14-423b-a8ff-b4e5633c2ca2" />

**PASO 2:** agrega la logica para la navegacion de la App en el archivo `AppNavigator.js` y **guardar** los cambios.
```js
// importar tabs
import AppTabs from '../navigation/AppTabs';

// importar screens que no se usan tabs
import LoginScreen from '../screens/LoginScreen';
import RegisterScreen from  '../screens/RegisterScreen';
import RegisterNewScreen from  '../screens/RegisterNewScreen';
import ViewNewScreen from '../screens/ViewNewScreen';

// importar react navigation
import { createStackNavigator } from '@react-navigation/stack';
import { NavigationContainer } from '@react-navigation/native';

// crear Stack y Componentes nativos
const Stack = createStackNavigator();
import { View, ActivityIndicator } from 'react-native';

// AuthContext
import { AuthProvider, useAuth } from '../context/AuthContext';

// Stack de autenticación (pantallas para usuarios no logueados)
const AuthStack = () => (
  <Stack.Navigator>
    <Stack.Screen name="Login" component={LoginScreen} options={{title: "Iniciar sesion"}}  />
    <Stack.Screen name="Register" component={RegisterScreen} options={{title:"Registrarse"}}  />
  </Stack.Navigator>
);

// Stack principal de la App (pantallas para usuarios logueados)
const AppStack = () => (
  <Stack.Navigator>
    <Stack.Screen name="Home" component={AppTabs} options={{ headerShown:false }}  />
    <Stack.Screen name="RegisterNew" component={RegisterNewScreen} options={{ title: "Registrar noticia" }}  />
    <Stack.Screen name="ViewNew" component={ViewNewScreen} options={{ title: "Ver noticia" }}  />
  </Stack.Navigator>
);

const RootNavigator = () => {
  const { user, loading } = useAuth(); // Obtiene el usuario y estado de carga

  // Mostramos un spinner mientras el AuthContext verifica el estado
  if (loading) {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
        <ActivityIndicator size="large" />
      </View>
    );
  }

  return (
    <NavigationContainer>
      {/* Si 'user' existe, muestra el AppStack, si no, muestra el AuthStack */}
      {user ? <AppStack /> : <AuthStack />}
    </NavigationContainer>
  );
};

export default function AppNavigator () {
  return (
    <AuthProvider>
      <RootNavigator />
    </AuthProvider>
  );
};
```

## Actualizaciones en el AppNavigator.js

1. Actualiza la importacion de Screens y navegacion usada (Tabs o Drawer).
<img width="855" height="216" alt="image" src="https://github.com/user-attachments/assets/df4b274f-fc41-4070-a6b3-ff3ddd37490b" />

2. Actualiza el **`AuthStack`** con las screens que **no requieren** iniciar sesion.
<img width="1427" height="219" alt="image" src="https://github.com/user-attachments/assets/2c3b8ba9-9c26-489f-972e-b956b39f524f" />

3. Actualiza **`AppStack`** con las screens que **requieren** iniciar sesion.
<img width="1424" height="217" alt="image" src="https://github.com/user-attachments/assets/6b29ec1e-1a01-41f9-9ec6-131d186c9c84" />


## Distribucion en Tabs o Drawer

**NOTA:** recuerda que la navegacion personalizada (Tabs o Drawer) tambien crea rutas de navegacion. 

Distribucion de screens:
- **AuthStack**: LoginScreen y RegisterScreen.
- **AppStack**: AppTabs **(** NewScreen y ProfileScreen **)**, RegisterNewScreen y ViewNewScreen.


