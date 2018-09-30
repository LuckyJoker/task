# 关于团队代码规范

### 工具的安装和使用

#### 1. 使用`ESLint`检查`JavaScript`代码

全局安装

`npm i -g eslint babel-eslint eslint-config-standard eslint-config-standard-react eslint-plugin-standard eslint-plugin-react eslint-plugin-promise eslint-plugin-import eslint-plugin-node`

配置文件
- eslint配置一个独立的[.eslintrc.yaml](./config_files/.eslintrc.yaml)文件，放在项目文件夹或者用户文件夹的根路径下

vscode插件配置

   首先，安装`ESLint`插件

   在设置中，将`eslint.autoFixOnSave`设置为`true`

 对于不需要代码检查的文件，可以将文件路径写在单独的`.eslintignore`的纯文本文件中，并将文件放在项目文件夹的根路径下。

#### 2. 使用`TSLint`检查`TypeScript`代码

全局安装

`npm i -g tslint`

tslint配置一个独立的[.tslint.yaml](./config_files/.tslint.yaml)文件，放在项目文件夹或者用户文件夹的根路径下

   vscode插件配置

   首先，安装`TSLint`插件

   在设置中，将`tslint.autoFixOnSave`设置为`true`

   对于不需要代码检查的文件，可以将文件路径写在单独的`.tslintignore`的纯文本文件中，并将文件放在项目文件夹的根路径下。

#### 3. prettier

prettier是一个更强力的代码格式化工具，在前面的基础上全局安装prettier。

- `npm i -g prettier`

- 在vscode中安装`Prettier - Code formatter`插件，之后使用`alt + shift + f`快捷键格式化代码时，prettier会对代码进行格式化

- prettier配置一个独立的[.prettierrc.yaml](./config_files/.prettierrc.yaml)文件，放在项目文件夹或者用户文件夹的根路径下


1. **代码规范**

      [Airbnb JavaScript Style Guide](https://github.com/yuche/javascript)

