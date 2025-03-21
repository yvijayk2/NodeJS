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
- Execute the following command to create an Angular workspace. Replace <version> with Angular CLI version.
  ```
  npx @angular/cli@<version> new angularMicroUiWorkspace --no-create-application
  ```
- Execute the following command to create an Angular workspace with a PNPM package manager instead of an NPM
  ```
  npx @angular/cli@<version> new angularMicroUiWorkspace --no-create-application --package-manager=pnpm
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
- - Install PNPM on Windows via PowerShell
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

- Execute the following command to create an NX Angular workspace using PNPM.\
  ```
  pnpx create-nx-workspace@<version> angularMicroUiWorkspace
  ```
  or use the following NPM command to create NX Angular
  ```
  npx create-nx-workspace@<version> angularMicroUiWorkspace --package-manager=pnpm
  ```
- - Refer to the Angular and NX version matrix to use the proper NX version to install the required Angular CLI
- - - Angular and NX version matrix
  https://nx.dev/nx-api/angular/documents/angular-nx-version-matrix

- Execute the following command to start the project
  ```
  pnpm start
  ```
### 


