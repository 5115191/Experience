## 1.React Native更改代码后运行或者打包后代码不生效
* 原因：android/app/src/main/assets下的index.android.bundle文件没有更新
* 解决办法：
  - 1. 进入android目录 `cd android `
   - 2. 运行`react-native bundle --platform android --dev false --entry-file index.js --bundle-output app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/`
*  或者在项目根目录运行`react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/`
*  如果项目中有index.android.js，那么运行
 `react-native bundle --platform android --dev false --entry-file index.android.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res/`
 
 ## 2.报错 React native : Unexpected token in JSON at position 0
 ### 解决办法：
 * 运行 `npm start -- --reset-cache` 重置缓存后启动npm
