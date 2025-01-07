## babel config



*babel.config.js*

module.exports = {

  presets: ['module:@react-native/babel-preset'],

  plugins: ['react-native-reanimated/plugin']

};


## SSR 
1. Navigate to `node_modules/native-base/src/core/NativeBaseProvider.tsx`.
2. Delete the `<SSRProvider></SSRProvider>` that wraps `{children}`. Take care not to delete `{children}`.
3. Remove the `SSRProvider` import. That is, delete this line: `import { SSRProvider } from '@react-native-aria/utils';`.
4. Run `npx patch-package native-base`. Select 'yes' in the prompt.
   
## Virtualized List
Virtualized List hatası


https://stackoverflow.com/questions/44743904/virtualizedlist-you-have-a-large-list-that-is-slow-to-update


You have a large list that is slow to update
bunu arat komple yoruma al yormasın seni

![[Pasted image 20240626052316.png]]


## Genel

const DismissKeyboard = ({ children }: any) => (

  <TouchableWithoutFeedback onPress={() => Keyboard.dismiss()}>

    {children}

  </TouchableWithoutFeedback>

)


tsconfig olayında ctrl+shift+P  restart ts server

genel manada da reload window


## ScrollListler

https://github.com/facebook/react-native/issues/31697#issuecomment-1150831275

![[Pasted image 20240524004309.png]]


## Ses

https://alexb72.medium.com/how-to-add-sound-to-react-native-8ef152ba1a6

## React Native TabView, The Issue of Centering When Clicking The TabBar Button

"node_modules\react-native-tab-view\src\TabBar.tsx"

![image](https://github.com/react-navigation/react-navigation/assets/115392938/92e493d0-29cc-4848-8393-0ea7b75a6e96)

The above code is causing the tab to center, and we're forced to wait for it.



#### And I did't want a feedback from the button, I fixed it like this ->


## React Native TabView, Preventing feedback when clicking the TabBar button


"node_modules\react-native-tab-view\src\PlatformPressable.tsx"

![image](https://github.com/react-navigation/react-navigation/assets/115392938/2ba823c6-92cd-4239-b39d-0e9b1dc4a423)


https://github.com/react-navigation/react-navigation/issues/11047