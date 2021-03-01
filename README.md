# NgComponent

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 11.2.2.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.


使用ng-packagr发布第三方包
npm install ng-packagr --save-dev
yarn add ng-packagr
在 ng-package.json 文件中添加如下内容：

{
  "$schema": "./node_modules/ng-packagr/ng-package.schema.json",
  "lib": {
    "entryFile": "public_api.ts"
  }
}
在 public_api.ts 文件中导出 header.module.ts

内容如下：

export * from './src/app/modules/header/header.module'
在 package.json 文件中的 scripts添加 "packagr": "ng-packagr -p ng-package.json" ，告诉 ng-packagr 根据 ng-package.json 来打包我们的组件库。同时，设置 "private": false
运行 npm run packagr 创建组件包，创建完成后会在项目的根目录中生成 dist 文件夹，里面的内容就是我们生成的标准的 Angular 组件库的结构。

进入 dist 目录执行 npm pack打包组件库，打包完成后，会在项目的根目录生成 my-component-library-0.0.0.tgz，0.0.0来至于 package.json 文件中一部分。


