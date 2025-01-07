npx react-native start --experimental-debugger

react-native run-android --terminal cmd

npx react-native start --reset-cache


bunu sık kullan:
cd android; ./gradlew clean; cd..

cd android ./gradlew clean ./gradlew build cd .. npx react-native run-android



gradle düzenlemesi:
https://stackoverflow.com/questions/51610420/deprecated-gradle-features-were-used-in-this-build-making-it-incompatible-with

cd android && ./gradlew clean && ./gradlew :app:bundleRelease
./gradlew build --warning-mode all
