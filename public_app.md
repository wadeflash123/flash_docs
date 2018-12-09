内测：com.tianxgjtest.goleteam，正式：com.tianxgjpublic.goleteam

热更新安装依赖
// npm install -g cordova-hot-code-push-cli
// cordova plugin add cordova-hot-code-push-plugin

cordova create cordovaApp com.cordova.testapp
cd cordovaApp
cordova platform add android
vue项目dist下的文件拷贝到www目录，index.html添加<script type="text/javascript" src="cordova.js"></script>
cordova-hcp build

1:然后执行 cordova build 打包你的项目。这样你的项目就可以热更新了。
2:现在修改cordova项目的js代码测试一下，例如加个alert('success');然后重新执行cordova-hcp build。
3:把你cordova项目中www上传到服务器放置热更新代码的位置，再打开你的app就会自动更新了。


cordova create ziyunapp com.example.ziyunapp ZiYun  cordova platform add android@^5.0.0

cordova plugin add cordova-plugin-statusbar
cordova plugin add cordova-plugin-splashscreen
cordova plugin add cordova-plugin-inappbrowser
cordova plugin add cordova-hot-code-push-plugin
cordova plugin remove cordova-hot-code-push-plugin
/** do not edit
密钥库：public12345
test密钥：public12345
ziyunapp http://app1.zysj38.com/ 天祥国际
cordova build android
keytool -genkey -v -keystore public-key.keystore -alias tianxgjpublic -keyalg RSA -keysize 2048 -validity 10000
cordova build android --release
jarsigner -verbose -digestalg SHA1 -sigalg SHA1withRSA -tsa http://sha256timestamp.ws.symantec.com/sha256/timestamp -keystore public-key.keystore platforms/android/app/build/outputs/apk/release/app-release-unsigned.apk tianxgjpublic

cordova build android --release -- --keystore="public-key.keystore" --alias=tianxgjpublic --storePassword=public12345 --password=public12345
**/
