## 1.React Native更改代码后运行或者打包后代码不生效
* 原因：android/app/src/main/assets下的index.android.bundle文件没有更新
* 解决办法：
  - 1. 进入android目录 `cd android `
    2. 运行`react-native bundle --platform android --dev false --entry-file index.js --bundle-output app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/`
  -  或者在项目根目录运行`react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/`
  -  如果项目中有index.android.js，那么运行
 `react-native bundle --platform android --dev false --entry-file index.android.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/`
 
 ## 2.报错 React native : Unexpected token in JSON at position 0
 * 解决办法：
   - 运行 `npm start -- --reset-cache` 重置缓存后启动npm
## 3.打包apk时（`./android/gradlew assembleRelease`）出错
 * 报错信息
 ` What went wrong: Execution failed for task ':app:mergeReleaseResources'.`

    - `[drawable-xhdpi-v4/node_modules_reactnavigation_src_views_assets_backicon] /Users/Ilyakar/Documents/Business/Development/My_Projects/new/Einee/App/android/app/src/main/res/drawable-xhdpi/node_modules_reactnavigation_src_views_assets_backicon.png [drawable-xhdpi-v4/node_modules_reactnavigation_src_views_assets_backicon] /Users/Ilyakar/Documents/Business/Development/My_Projects/new/Einee/App/android/app/build/generated/res/react/release/drawable-
.................`

* 解决办法
  - 1.删除**android/app**目录下的**build**文件夹
  - 2.删除**android**目录下的**build**文件夹
  - 3.运行`rm -rf $HOME/.gradle/caches/`
  - 4.打开**android/app**目录下的**build.gradle**文件
  - 5.注释掉下面的代码
    - `apply from: "../../node_modules/react-native/react.gradle"`
  - 6.删除**assets**目录下的`index.android.bundle`文件
  - 7.重新生成`index.android.bundle`文件
    - `react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res`
  - 8.运行`cd android`和`gradlew assembleRelease`进行打包
