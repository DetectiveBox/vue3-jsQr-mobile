# 技术栈： Vue 3 + TypeScript + Vite + jsQr

#### 使用说明见代码注释，本人透明小菜，欢迎大佬指点！

## 本项目的UI组件用的是 arco-design，可以根据需要改成自己需要的--------P.S. 本项目在PC端可以测试，扫描二维码成功，但是移动端的话需要在https协议使用！！！ 

## 如果要在PC端运行测试，请注释掉  GetQrcode.vue 52行

##  参考项目： https://ext.dcloud.net.cn/plugin?id=7007      https://ask.dcloud.net.cn/article/35409
    因为公司项目需要手机浏览器扫描二维码的功能，网上好多博客的方法没法用，直到看到木木大神的项目，但是可能是由于本人太菜，下载下来使用的时候还是有点问题，所以想在大佬原项目的基础上结合自己遇到的问题修改一下，来个开箱即用的，符合拿来主义的需求。

##  功能： 移动端浏览器调用本地摄像头，扫描并识别二维码，支持安卓手机、苹果手机常见浏览器

##  HelloWorld.vue 为主页面，GetQrcode.vue 为调用摄像头的组件，可根据需要自己修改

## jsQr地址： https://github.com/cozmo/jsQR

## jsQ安装： https://www.npmjs.com/package/jsqr

## npm install

## npm run dev


This template should help get you started developing with Vue 3 and TypeScript in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar)

## Type Support For `.vue` Imports in TS

Since TypeScript cannot handle type information for `.vue` imports, they are shimmed to be a generic Vue component type by default. In most cases this is fine if you don't really care about component prop types outside of templates. However, if you wish to get actual prop types in `.vue` imports (for example to get props validation when using manual `h(...)` calls), you can enable Volar's Take Over mode by following these steps:

1. Run `Extensions: Show Built-in Extensions` from VS Code's command palette, look for `TypeScript and JavaScript Language Features`, then right click and select `Disable (Workspace)`. By default, Take Over mode will enable itself if the default TypeScript extension is disabled.
2. Reload the VS Code window by running `Developer: Reload Window` from the command palette.

You can learn more about Take Over mode [here](https://github.com/johnsoncodehk/volar/discussions/471).
