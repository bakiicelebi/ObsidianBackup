* Where:
Script 'C:\Users\Baki\OneDrive\Masa�st�\React-Native\FirstApp\node_modules\@react-native-community\cli-platform-android\native_modules.gradle' line: 391

* What went wrong:
A problem occurred evaluating script.
> node:internal/modules/cjs/loader:1146  throw err;  ^Error: Cannot find module 'C:\Users\Baki\OneDrive\MasaÃ¼stÃ¼\React-Native\FirstApp\node_modules\@react-native-community\cli\build\bin.js'    at Module._resolveFilename (node:internal/modules/cjs/loader:1143:15)    at Module._load (node:internal/modules/cjs/loader:984:27)    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:142:12)    at node:internal/main/run_main_module:28:49 {  code: 'MODULE_NOT_FOUND',  requireStack: []}Node.js v21.5.0
> 
> 29.12.2023  04:43



ts hatası ignore


<View style={{ position: 'absolute', flexDirection: "row", top: 20, left: 20 }}>

      {tabs.map((tab:any) => (

        <Button

          key={tab.key}

          title={tab.title}

          // @ts-ignore

          onPress={() => navigation.navigate(tab.key)} // useNavigation hook'u ile navigation nesnesine erişim sağla

        />

      ))}

    </View>