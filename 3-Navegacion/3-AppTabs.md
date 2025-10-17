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
        <Stack.Screen name="New" component={NewScreen} options={{ title: "Noticias" }}  />
        <Stack.Screen name="ViewNew" component={ViewNewScreen} options={{ title: "Ver Noticia" }}  />
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

**PASO 1:** instalar `vector-icons` e importarlo en el archivo **`📁nagivation > AppTabs.js`**.
```code
npm install react-native-vector-icons
```

<img width="1927" height="1027" alt="image" src="https://github.com/user-attachments/assets/ab35968a-7ffc-46b5-8467-fae8b596e742" />


**PASO 2:** editar en el archivo el `<Tab.Navigator>`.

```js
screenOptions={({ route }) => ({
    headerShown: false,
    tabBarShowLabel: true,
    tabBarActiveTintColor: '#0051CA', // color tabs
    tabBarInactiveTintColor: 'gray',

    // configurar icono segun name
    tabBarIcon: ({ color, size, focused }) => {
      let iconName;

      if (route.name === 'Login') {
        iconName = focused ? 'key' : 'key-outline';
      } else if (route.name === 'Register') {
        iconName = focused ? 'person' : 'person-outline';
      }

      return <Ionicons name={iconName} size={size} color={color} />;
    },
  })}  
```

<img width="1927" height="1087" alt="image" src="https://github.com/user-attachments/assets/9226d298-b8ad-4029-8e26-c439643a447e" />

**PASO 3:** iniciar la app y verifica que funcionen los tabs.

### Tab > LoginScreen 
<img width="463" height="812" alt="image" src="https://github.com/user-attachments/assets/d8622119-5987-476c-abfe-f1ce6bbf5e60" />

### Tab > RegisterScreen 
<img width="451" height="813" alt="image" src="https://github.com/user-attachments/assets/05833fab-1225-47da-ba3a-025a461294d7" />
