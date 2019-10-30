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

## Cordoca commands (inside container)

> IMPORTANT all command in **/tmp** folder

create new cordova app  
```
cd /tmp
cordova create MyApp
cd MyApp
```

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

run android emulator
```
open AndroidStudio application and run Tools > AVD Manager
```

install app on android emulator
```
/Users/.../Library/Android/sdk/platform-tools/adb install /Users/.../other/docker_cordova_android/build/MyApp/platforms/android/app/build/outputs/apk/debug/app-debug.apk
```

