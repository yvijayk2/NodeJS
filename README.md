# User guide to use NodeJS to create an Angular project

## NVM to manage Node versions
Use the NVM (Node Version Manager) to manage NodeJS versions.\
Follow the steps given in the following link to set up NVM:\
https://github.com/nvm-sh/nvm

### NVM commands
#### To list the Node version
```
nvm list
```
##### Sample output
* 23.9.0 (Currently using 64-bit executable)\
20.11.1\
20.5.0\
18.17.0\
18.13.0\
  
#### To use a Node version (20.11.1)
```
nvm use 20.11.1
```

### Create an Angular project using NPM
- Go to a folder
- Create a package.json file with the following content
  ```
  {
    "name": "UI",
    "version": "1.0.0",
    "scripts": {
      "ng": "ng"
    }
  }
  ```
- Execute the following command to install the latest Angular CLI
  ```
  npm install --save @angular/cli
  ```
 #### Create an Angular workspace for re-usable libraries which are used by micro modules
 - Execute the following command to the workspace
    ```
    npm run ng new microuiWorkspace --create-application="false"
    ```
    or
    ```
    npm run ng new microuiWorkspace --no-create-application
    ```
 - Execute the following command to create a micro application (order and product) in the microuiWorkspace workspace
    ```
    cd microuiWorkspace
    npm run ng generate application order --routing
    npm run ng generate application product --routing
    ```

  #### Install Webpack CLI
  - Execute the following command to install Webpack CLI
    ```
    npm install webpack webpack-cli --save-dev
    ```
  #### Now add the micro application to Angular module federation to run the application as independent projects
  - Execute the following command to add the application to Angular module federation
    ```
    npm run ng add @angular-architects/module-federation --project order --port 4201
    npm run ng add @angular-architects/module-federation --project product --port 4202
    ```

### Create an Angular project using NX and PNPM
- Install PNPM following the steps given below if PNPM is not
- - Install PNPM on Windows via powershell
    ```
    Invoke-WebRequest https://get.pnpm.io/install.ps1 -UseBasicParsing | Invoke-Expression
    ```
- - Install PNPM on Unix
    ```
    curl -fsSL https://get.pnpm.io/install.sh | sh -
    ```
- - Install PNPM using NPM
    ```
    npm install -g pnpm
    ```

- Execute the following command to create an Angular workspace.\
  Refer to Angular and NX version matrix to use proper NX version to install required Angular CLI
  ```
  npx create-nx-workspace@latest angularMicroUiWorkspace --package-manager=pnpm
  npx @angular/cli@<version> new angularMicroUiWorkspace --no-create-application --package-manager=pnpm
  ```
- - - Angular and NX version matrix
  https://nx.dev/nx-api/angular/documents/angular-nx-version-matrix

