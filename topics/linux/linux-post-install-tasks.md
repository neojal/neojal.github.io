# Linux Post Install Tasks and Development Environment
_Executing bash in Windows10!_

### Install VIM editor

- Install VIM editor
- Install vimrc, _The Ultimate Vim configuration_: [https://github.com/amix/vimrc](https://github.com/amix/vimrc)

### Install NodeJS

1. Add the repository, you can specify the required version:
    ```
    $ curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
    ```
2. Install:

    ```
    $ sudo apt-get install nodejs
    ``` 
3. Enjoy:

    ```
    $ node -v
    v8.7.0
    $ npm -v
    5.4.2
    ```
### Install Angular CLI
* Using the npm package manager to install globally the Angular CLI:
    ```
    $ sudo npm install -g @angular/cli
    ```