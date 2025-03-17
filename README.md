# User guide to use NodeJS to create an Angular project

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

### Create an Angular project
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




