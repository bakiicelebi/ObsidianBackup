
![[C3AF5316-BC55-40FB-AC6D-91BE1CDF3346.png]]


``` react-native
import * as React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';

import Dashboard from './Dashboard';
import UserList from './UserList';
import RoleList from './RoleList';
import SystemConfiguration from './SystemConfiguration';
import Login from './Login';
import FormTest from './FormTest';
import MaterialReactTableTest from './MaterialReactTableTest';
import NotFound from './NotFound';

const Stack = createStackNavigator();

function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator initialRouteName="Dashboard">
        <Stack.Screen name="Dashboard" component={Dashboard} />
        <Stack.Screen name="UserList" component={UserList} />
        <Stack.Screen name="RoleList" component={RoleList} />
        <Stack.Screen name="SystemConfiguration" component={SystemConfiguration} />
        <Stack.Screen name="Login" component={Login} />
        <Stack.Screen name="FormTest" component={FormTest} />
        <Stack.Screen name="MaterialReactTableTest" component={MaterialReactTableTest} />
        <Stack.Screen name="NotFound" component={NotFound} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}

export default App;

```




