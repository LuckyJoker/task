# 关于团队代码规范

### 工具的安装和使用

1. **eslint、tslint**

   全局安装

   `npm i -g eslint babel-eslint eslint-plugin-import eslint-plugin-react eslint-plugin-jsx-a11y eslint-config-airbnb tslint`

   配置文件
   - eslint配置一个独立的`.eslintrc.yaml`文件，放在项目文件夹或者用户文件夹的根路径下

   ```yaml
   ---
   extends: airbnb
   parser: babel-eslint
   plugins:
    - react
    - jsx-a11y
    - import
   env:
    amd: true
    browser: true
    jquery: true
    node: true
    es6: true
    worker: true
   rules:
    no-console: off
    max-len: off
    require-jsdoc: warn
    func-names: off
    indent:
     - error
     - tab
     - SwitchCase: 1
       ignoredNodes:
        - JSXElement
        - JSXElement *
    no-tabs: 0
   ```

   - tslint配置一个独立的`.tslint.yaml`文件，放在项目文件夹或者用户文件夹的根路径下

   ```yaml
   ---
   rulesDirectory:
    - node_modules/codelyzer
   rules:
    arrow-return-shorthand: true
    callable-types: true
    class-name: true
    comment-format:
     - true
     - check-space
    curly: true
    deprecation:
     severity: warn
    eofline: true
    forin: true
    import-blacklist:
     - true
     - rxjs
     - rxjs/Rx
    import-spacing: true
    indent:
     - true
     - spaces
    interface-over-type-literal: true
    label-position: true
    max-line-length:
     - true
     - 140
    member-access: false
    member-ordering:
     - true
     - order:
       - static-field
       - instance-field
       - static-method
       - instance-method
    no-arg: true
    no-bitwise: true
    no-console:
     - true
     - debug
     - info
     - time
     - timeEnd
     - trace
    no-construct: true
    no-debugger: true
    no-duplicate-super: true
    no-empty: false
    no-empty-interface: true
    no-eval: true
    no-inferrable-types:
     - true
     - ignore-params
    no-misused-new: true
    no-non-null-assertion: true
    no-shadowed-variable: true
    no-string-literal: false
    no-string-throw: true
    no-switch-case-fall-through: true
    no-trailing-whitespace: true
    no-unnecessary-initializer: true
    no-unused-expression: true
    no-use-before-declare: true
    no-var-keyword: true
    object-literal-sort-keys: false
    one-line:
     - true
     - check-open-brace
     - check-catch
     - check-else
     - check-whitespace
    prefer-const: true
    quotemark:
     - true
     - single
    radix: true
    semicolon:
     - true
     - always
    triple-equals:
     - true
     - allow-null-check
    typedef-whitespace:
     - true
     - call-signature: nospace
       index-signature: nospace
       parameter: nospace
       property-declaration: nospace
       variable-declaration: nospace
    unified-signatures: true
    variable-name: false
    whitespace:
     - true
     - check-branch
     - check-decl
     - check-operator
     - check-separator
     - check-type
    directive-selector:
     - true
     - attribute
     - app
     - camelCase
    component-selector:
     - true
     - element
     - app
     - kebab-case
    no-output-on-prefix: true
    use-input-property-decorator: true
    use-output-property-decorator: true
    use-host-property-decorator: true
    no-input-rename: true
    no-output-rename: true
    use-life-cycle-interface: true
    use-pipe-transform-interface: true
    component-class-suffix: true
    directive-class-suffix: true
   ```

   vscode插件配置

   首先，安装`ESLint`和`TSLint`两个插件

   在设置中，将`tslint.autoFixOnSave`和`eslint.autoFixOnSave`设置为`true`

   对于不需要代码检查的文件，可以将路径写在单独的`.eslintignore`或者`.tslintignore`的纯文本文件中，并将文件放在项目文件夹的跟路径下。

2. **prettier**

      prettier是一个更强力的代码格式化工具，在前面的基础上全局安装prettier。

      - `npm i -g prettier`

      - 在vscode中安装`Prettier - Code formatter`插件，之后使用`alt + shift + f`快捷键格式化代码时，prettier会对代码进行格式化

      - prettier配置一个独立的`.prettierrc.yaml`文件，放在项目文件夹或者用户文件夹的根路径下

        ```yaml
        ---
        useTabs: true
        semi: true
        singleQuote: true
        trailingComma: es5
        bracketSpacing: true
        jsxBracketSameLine: false
        arrowParens: avoid
        insertPragma: true
        ```

3. **代码规范**

      [Airbnb JavaScript Style Guide](https://github.com/yuche/javascript)

