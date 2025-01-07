import { NavigationContainer } from '@react-navigation/native';

import { createMaterialTopTabNavigator } from "@react-navigation/material-top-tabs"

const TopTab = createMaterialTopTabNavigator();


const TopBar = () => {

    return (

        <TopTab.Navigator screenOptions={{

            tabBarItemStyle:{width:120},

            tabBarScrollEnabled: true, // İstediğiniz genişliği ayarlayabilirsiniz

            tabBarIndicatorStyle: { backgroundColor: 'yellow' }, // İstenirse seçili olan tab'ın alt çizgisinin rengi ayarlanabilir

        }}>

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsPage' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsPage2' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsPage3' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsPsages' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsPdage2' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsPcage3' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsPaage' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsfPage2' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsPzage3' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsP3age' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsPaage2' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsxPage3' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsP2age' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealsPawge2' component={Meals} />

            <TopTab.Screen options={{ title: 'Meals' }} name='MealbsPage3' component={Meals} />

        </TopTab.Navigator>

    )

}