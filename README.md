# GoBarber Mobile

### Remover versão global do react-native-cli

Não instalar o react-native-cli de forma global. Caso tenha instalado, remover:
* $ npm uninstall -g react-native-cli
* $ yarn global remove react-native-cli

### Criar projeto com npx

* $ npx react-native init appgobarber --template react-native-template-typescript

### Executar projeto
* Windows/Android abrir emulador antes de executar
    * $ yarn android
* Mac executar diretamente
    * $ yarn ios

### Ajustes no projeto inicial
* Criar novo App.tsx limpo em src e mudar App e index.js
* Remover arquivos de configuração
    * .eslintrc.js
    * .prettierrc.js

### Configurar padrões

* $ yarn add eslint -D
* $ yarn eslint --init

```
? How would you like to use ESLint? To check syntax, find problems, and enforce code style
? What type of modules does your project use? JavaScript modules (import/export)
? Which framework does your project use? React
? Does your project use TypeScript? Yes
? Where does your code run?
? How would you like to define a style for your project? Use a popular style guide
? Which style guide do you want to follow? Airbnb: https://github.com/airbnb/javascript
? What format do you want your config file to be in? JSON
Checking peerDependencies of eslint-config-airbnb@latest
The config that you've selected requires the following dependencies:

eslint-plugin-react@^7.19.0 @typescript-eslint/eslint-plugin@latest eslint-config-airbnb@latest eslint@^5.16.0 || ^6.8.0 eslint-plugin-import@^2.20.1 eslint-plugin-jsx-a11y@^6.2.3 eslint-plugin-react-hooks@^2.5.0 || ^1.7.0 @typescript-eslint/parser@latest
? Would you like to install them now with npm? No
```

* $ yarn add - D eslint-plugin-react@^7.19.0 @typescript-eslint/eslint-plugin@latest eslint-config-airbnb@latest eslint-plugin-import@^2.20.1 eslint-plugin-jsx-a11y@^6.2.3 eslint-plugin-react-hooks@^2.5.0 @typescript-eslint/parser@latest

* $ yarn add -D prettier eslint-config-prettier eslint-plugin-prettier

* $ yarn add -D eslint-import-resolver-typescript

* Copiar os arquivos de configuração do projeto WEB para o projeto Mobile:
    * .editorconfig
    * .eslintignore
    * .eslintrc.json
      * Retirar a linha browser em Env
        * ```
          "env": {
            "browser": true,
            "es6": true
          },
          ```
    * prettier.config.js

* Recarregar VSCode (Ctrl + Shift + P >> Reload Window)

### Para IOS necessário rodar comandos para o React-Navigation

```
$ cd ios
$ pod install
  * cocoapods (cocoapods.org) precisa estar instalado
    * $ sudo gem install cocoapods
```

### Instalar Fonts

* Baixar fontes
* Salvar na raiz do projeto em /assets/fonts o TTFs desejados
  * ficar atento ao nome do arquivo para Android e IOS
  * Não é a mesma pasta assets do SRC
* Criar e configurar o react-native.config.js no raiz
* $ yarn react-native link

### Instalar icons (apenas IOS, no android é automatico)

* $ cd ios
* $ pod install
* $ /ios/appgobarber/info.plist
  * incluir "<string>Feather.ttf</string>":
  * ```
    <key>UIAppFonts</key>
      <array>
        <string>RobotoSlab-Medium.ttf</string>
        <string>RobotoSlab-Regular.ttf</string>
        <string>Feather.ttf</string>
      </array>
    ```

### Ajustar /android/app/build.gradele

* incluir na ultima linha
  * ```
    project.ext.vectoricons = [
      iconsFontNames: ['Feather.ttf']
    ];

    apply from: "../../node_modules/react-native-vector-icons/fonts.gradle"
    ```

### Configurar endereço do backend (baseURL: 'http://?:3333')

```
* iOS com Emulador: localhost
* iOs com fisico: IP da maquina
* Android com Emulador: localhost ($ adb reverse tcp:3333 tcp:3333)
* Android com Emulador: 10.0.2.2 (Android Studio)
* Android com Emulador: 10.0.3.2 (Genymotion)
* Android com fisico: IP da maquina
```

### Add AsyncStorage (in IOS)

* $ cd ios
* $ pod install

### .
### .
### .

### *****************************************************************
### >>>>>>> README.md projetos anteriores

# GoBarber Web

GoBarber Web Project - BootCamp April/2020 (by RocketSeat)

###  Initial commit with react-app-typescript-template

* copy
  * .editorconfig
  * .eslintignore
  * .eslintrc.json
  * prettier.config.js

* include devdependence in package.json

```
 "devDependencies": {
    "@types/react-router-dom": "^5.1.4",
    "@types/styled-components": "^5.1.0",
    "@typescript-eslint/eslint-plugin": "^2.29.0",
    "@typescript-eslint/parser": "^2.29.0",
    "eslint": "^6.8.0",
    "eslint-config-airbnb": "^18.1.0",
    "eslint-config-prettier": "^6.11.0",
    "eslint-import-resolver-typescript": "^2.0.0",
    "eslint-plugin-import": "2.20.1",
    "eslint-plugin-jsx-a11y": "6.2.3",
    "eslint-plugin-prettier": "^3.1.3",
    "eslint-plugin-react": "7.19.0",
    "eslint-plugin-react-hooks": "2.5.0",
    "prettier": "^2.0.5"
  }
```




#

## README.md projetos anteriores


## Ambiente de desenvolvimento

* Node
* Yarn
* Visual Studio Code
    * Dracula
    * Material icon Theme
    * Jira Code Font

```
const path = require('path')
path.resolve(__dirname, 'src', 'index.js')
use o path ao inves de ./src/index.js devivo as diferenças entre SOs
```

## Criar projeto NodeJs com TypeScript

```
$ mkdir pasta-projeto
$ cd pasta-projeto
$ yarn init -y
$ yarn add express
$ yarn add -D @types/express typescript ts-node-dev eslint-import-resolver-typescript
$ yarn tsc --init

Configurar tsconfig.json
    "outDir": "./dist",
    "rootDir": "./src",

Configurar script no package.json
    "scripts": {
        "build": "tsc",
        "dev:server":"ts-node-dev --transpileOnly --ignore-watch node-modules src/server.ts"
    },

Configurar .eslintrc.json
    "rules": {
        "import/extensions": [
        "error",
        "ignorePackages",
        {
            "ts": "never"
        }
        ]
    },
    "settings": {
        "import/resolver": {
        "typescript": {}
        }
    }

```

## Padronizar projeto

```
* Instalar plugin "EditorConfig for VS Code"
* Botão direito na pasta do projeto e escolher "Generate .editorconfig"

```
root = true

[*]
indent_style = space
indent_size = 2
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
end_of_line = lf
```

* Instalar plugin "ESLint"


$ yarn add eslint -D

$ yarn eslint --init
    ? How would you like to use ESLint? To check syntax, find problems, and enforce code style
    ? What type of modules does your project use? JavaScript modules (import/export)
    ? Which framework does your project use? None of these
    ? Does your project use TypeScript? Yes
    ? Where does your code run? Node
    ? How would you like to define a style for your project? Use a popular style guide
    ? Which style guide do you want to follow? Airbnb: https://github.com/airbnb/javascript
    ? What format do you want your config file to be in? JSON
    ? Would you like to install them now with npm? No

$ yarn add -D @typescript-eslint/eslint-plugin@latest eslint-config-airbnb-base@latest eslint-plugin-import@^2.20.1 @typescript-eslint/parser@latest

* atualizar settings.json
    "[javascript]": {
        "editor.codeActionsOnSave": {
            "source.fixAll.eslint": true,
        }
    },
    "[javascriptreact]": {
        "editor.codeActionsOnSave": {
            "source.fixAll.eslint": true,
        }
    },
    "[typescript]": {
        "editor.codeActionsOnSave": {
            "source.fixAll.eslint": true,
        }
    },
    "[typescriptreact]": {
        "editor.codeActionsOnSave": {
            "source.fixAll.eslint": true,
        }
    },
```

### Prettier

$ yarn add -D prettier eslint-config-prettier eslint-plugin-prettier

Configurar .eslintrc.json
    ...
    "extends": [
        "airbnb-base",
        "plugin:@typescript-eslint/recommended",
        "prettier/@typescript-eslint",
        "plugin:@prettier/recommended"
    ],
    ...
    "plugins": [
        "@typescript-eslint",
        "prettier"
    ],
    ...
    "rules": {
        "prettier/prettier": "error",
        "import/extensions": [
            "error",
            "ignorePackages",
            {
                "ts": "never"
            }
        ]
    },

Criar prettier.config.js
	module.exports = {
		singleQuote: true,
		trailingComma: "all",
		arrowParens: "avoid",
	};


### Debug

* Na guia lateral Run (bug) clicar em "create a launch.json file

```
{
  // Use IntelliSense to learn about possible attributes.
  // Hover to view descriptions of existing attributes.
  // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "attach",
      "protocol": "inspector",
      "restart": true,
      "name": "Debug",
      "skipFiles": [
        "<node_internals>/**"
      ],
      "outFiles": [
        "${workspaceFolder}/**/*.js"
      ]
    }
  ]
}
```

* Atualizar package.json

```
"dev:server": "ts-node-dev --inspect --transpileOnly --ignore-watch node-modules src/server.ts"
```

### Lembretes

* Migration
  * yarn typeorm migration:create -n CreateAppointments
  * yarn typeorm migration:run
  * yarn typeorm migration:revert

### Conceitos

* SoC - Separation of Concerns
* DTO - Data Transfer Object
* SOLID
  * Single Responsability Principle
  * O
  * L
  * I
  * Dependecy Inversion Principle
* DRY - Don't Repeat Yourself
* KISS - Keep It Simple & Stupid

### Links

* http://www.md5.cz/ - Online generator md5 hash of a string
* https://jwt.io/ - JWT.IO allows you to decode, verify and generate JWT.


## Create React App

* npm i -g create-react-app
* create-react-app 05-primeiro-projeto-react --template=typescript

## Padronizar projeto React JS

* Instalar plugin "EditorConfig for VS Code"
* Botão direito na pasta do projeto e escolher "Generate .editorconfig"

```
root = true

[*]
indent_style = space
indent_size = 2
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
end_of_line = lf
```

* $ yarn add eslint -D

* Excluir configuração do package.json
  "eslintConfig": {
    "extends": "react-app"
  },

* yarn eslint --init

```
? How would you like to use ESLint? To check syntax, find problems, and enforce code style
? What type of modules does your project use? JavaScript modules (import/export)
? Which framework does your project use? React
? Does your project use TypeScript? Yes
? Where does your code run? Browser
? How would you like to define a style for your project? Use a popular style guide
? Which style guide do you want to follow? Airbnb: https://github.com/airbnb/javascript
? What format do you want your config file to be in? JSON
? Would you like to install them now with npm? No
```

* $ yarn add -D eslint-plugin-react@^7.19.0 @typescript-eslint/eslint-plugin@latest eslint-config-airbnb@latest eslint-plugin-import@^2.20.1 eslint-plugin-jsx-a11y@^6.2.3 eslint-plugin-react-hooks@^2.5.0 @typescript-eslint/parser@latest

* criar .eslintgnore
```
**/*.js
node_modules
build
```

* editar .eslintrc.json

* $ yarn add -D eslint-import-resolver-typescript

* $ yarn add -D prettier eslint-config-prettier eslint-plugin-prettier

* criar prettier.config.js


### Dicas/Lembretes

* //eslint-disable-line
  desabilita a checagem do eslint na linha

### Extensions VSCode

* dzannotti.vscode-babel-coloring
* naumovs.color-highlight
* ricardo-emerson.create-react-tsx-component
* mikestead.dotenv
* dracula-theme.theme-dracula
* editorconfig.editorconfig
* dsznajder.es7-react-js-snippets
* dbaeumer.vscode-eslint
* wix.glean
* pkief.material-icon-theme
* ricardo-emerson.react-development-extensions-pack
* msjsdiag.vscode-react-native
* equimper.react-native-react-redux
* rocketseat.rocketseatreactnative
* rocketseat.rocketseatreactjs
* jpoissonnier.vscode-styled-components
* hookyqr.beautify

### settings.json VSCode

```
{
    "workbench.colorTheme": "Dracula",
    "workbench.iconTheme": "material-icon-theme",
    "workbench.startupEditor": "newUntitledFile",
    "terminal.integrated.fontSize": 14,
    "editor.tabSize": 2,
    "editor.fontSize": 18,
    "editor.lineHeight": 24,
    "editor.fontFamily": "Fira Code",
    "editor.fontLigatures": false,
    "explorer.compactFolders": false,
    "editor.renderLineHighlight": "gutter",
    "workbench.editor.labelFormat": "short",
    "extensions.ignoreRecommendations": true,
    "javascript.updateImportsOnFileMove.enabled": "never",
    "typescript.updateImportsOnFileMove.enabled": "never",
    "breadcrumbs.enabled": true,
    "editor.parameterHints.enabled": false,
    "explorer.confirmDragAndDrop": false,
    "explorer.confirmDelete": false,
    "editor.rulers": [
        80,
        120
    ],
    "[javascript]": {
        "editor.codeActionsOnSave": {
            "source.fixAll.eslint": true,
        }
    },
    "[javascriptreact]": {
        "editor.codeActionsOnSave": {
            "source.fixAll.eslint": true,
        }
    },
    "[typescript]": {
        "editor.codeActionsOnSave": {
            "source.fixAll.eslint": true,
        }
    },
    "[typescriptreact]": {
        "editor.codeActionsOnSave": {
            "source.fixAll.eslint": true,
        }
    },
    "git.enableSmartCommit": true,
    "window.zoomLevel": 0,
}
```
