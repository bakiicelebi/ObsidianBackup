


> @okwasniewski Have a look please,
> 
>  TestApp.mov




I faced the same issue yesterday, but I'm not sure if it's fixed dynamically.



## React Native TabView, The Issue of Centering When Clicking The TabBar Button

"node_modules\react-native-tab-view\src\TabBar.tsx"

![image](https://github.com/react-navigation/react-navigation/assets/115392938/92e493d0-29cc-4848-8393-0ea7b75a6e96)

The above code is causing the tab to center, and we're forced to wait for it.



#### And I did't want a feedback from the button, I fixed it like this ->


## React Native TabView, Preventing feedback when clicking the TabBar button


"node_modules\react-native-tab-view\src\PlatformPressable.tsx"

![image](https://github.com/react-navigation/react-navigation/assets/115392938/2ba823c6-92cd-4239-b39d-0e9b1dc4a423)


https://github.com/react-navigation/react-navigation/issues/11047