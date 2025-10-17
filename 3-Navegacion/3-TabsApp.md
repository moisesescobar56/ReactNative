# Navegacion con Tabs

## Instalar React Navigation [Stack] y [Tabs]

**PASO 1:** Instalar el paquete npm React Navigation [Stack] y [Tabs]
```code
npm install @react-navigation/stack
npm install @react-navigation/bottom-tabs
```

**PASO 2:** Instalar el paquete npm de gestos.
```code
npx expo install react-native-gesture-handler react-native-reanimated react-native-worklets
```

**PASO 3:** editar el archivo **`📁nagivation > AppTabs.js`**.
```js
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';

// importar screens de los tabs
import LoginScreen from '../screens/LoginScreen';
import RegisterScreen from  '../screens/RegisterScreen';

// crear tabs
const Tab = createBottomTabNavigator();

// exportar tabs
export default function AppTabs() {
  return (
    <Tab.Navigator>
      <Tab.Screen name="Login" component={LoginScreen} options={{ title: "Iniciar sesión" }} />
      <Tab.Screen name="Register" component={RegisterScreen} options={{ title: "Registrarse" }} />
    </Tab.Navigator>
  );
}
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/1d78bc5f-9984-4823-b7fb-29c73597a2bc" />

**PASO 4:** editar el archivo **`App.js`**.
```js
// importar tabs
import AppTabs from './navigation/AppTabs';

// importar screens que no se usan en los tabs
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
        <Stack.Screen name="Home" component={AppTabs} options={{ headerShown: false }} />
        <Stack.Screen name="Register" component={NewScreen} options={{ headerShown: false }} />
        <Stack.Screen name="Register" component={ViewNewScreen} options={{ headerShown: false }} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/02891037-5c56-4ad7-a6fc-5fe0d60cf1b9" />

**PASO 5:** iniciar la app y verifica que funcionen los tabs.

### Tab > LoginScreen 
<img width="464" height="820" alt="image" src="https://github.com/user-attachments/assets/e735a068-0d4d-4329-b855-33382f04dfa6" />

### Tab > RegisterScreen 
<img width="458" height="816" alt="image" src="https://github.com/user-attachments/assets/9297a797-b155-4046-bfa4-aec563bf736f" />

## Implementar iconos
En proceso...
