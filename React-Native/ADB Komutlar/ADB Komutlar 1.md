- adb devices
- adb install (-r) android/app/build/outputs/apk/release/app-release.apk
- adb (-s RZ8N31B9BFY) uninstall com.measurement_system
- adb logcat
- adb logcat *:E

telefon wifisi üzerinden ;
- adb tcpip 5555
- (adb (-s RZ8N31B9BFY) tcpip 5555)
- adb connect 192.168.1.146:5555

