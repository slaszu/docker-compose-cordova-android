# Docker ready to build cordova apps for android platform

## Docker commands (outside container)

build  
```
docker-compose build --force-rm cordova
```

run  
```
docker-compose up -d
```

ssh into docker  
```
docker-compose exec cordova bash
```

## Cordova commands (inside container)

> IMPORTANT all command in **/tmp** folder

create new cordova app  
```
cd /tmp
cordova create MyApp
cd MyApp
```

### Browser (local app testing)  

add platform browser  
```
cd /tmp/MyApp  
cordova platform add browser  
```

run application in browser  
```
cd /tmp/MyApp  
cordova run browser  
```

> output from run process  

```
Static file server running @ http://localhost:8000/index.html  
CTRL + C to shut down  
```

> open http://localhost:8000/index.html  in your local browser (outside container)  


### Android (app building)  

add platform android
```
cd /tmp/MyApp
cordova platform add android
```

build application
```
cd /tmp/MyApp
cordova build android
```

> output from build process  

```
BUILD SUCCESSFUL in 3m 19s
47 actionable tasks: 47 executed
Built the following apk(s):
	/tmp/MyApp/platforms/android/app/build/outputs/apk/debug/app-debug.apk
```

## Android commands (outside container)

run android emulator (from Android Studio)
```
open AndroidStudio application and run Tools > AVD Manager
```

run android emulator (from cli)  
https://stackoverflow.com/questions/4974568/how-do-i-launch-the-android-emulator-from-the-command-line  


install app on android emulator
```
/Users/.../Library/Android/sdk/platform-tools/adb install /Users/.../other/docker_cordova_android/build/MyApp/platforms/android/app/build/outputs/apk/debug/app-debug.apk
```

## Update cordova (inside container)

```
npm install -g cordova
```

## Update android sdk (inside container)

todo:  
- update android sdk https://stackoverflow.com/questions/17963508/how-to-install-android-sdk-build-tools-on-the-command-line  

- accept sdkmanager --licenses https://stackoverflow.com/questions/38096225/automatically-accept-all-sdk-licences  


```
android update sdk -u
```  
> -u - from cli (do not show gui)
