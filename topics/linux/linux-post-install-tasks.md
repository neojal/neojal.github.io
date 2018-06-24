# Install Manjaro

(Or the fun of don't having any plan to hang on saturday night)

### Requirements
- Download you favourite distro ISO. Mine is [Manjaro KDE Edition](https://manjaro.org/get-manjaro/).
- While downloading the ISO, go to the fridge or closest store to get a fresh beer! 
  - but don't forget your keys or phone... just in case ;)
- Create a bootable USB unit with [YUMI – Multiboot USB Creator](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/)
  - Use the latest YUMI version available!

### Install Manjaro
- Pretty straight forward

### Linux Post Install Tasks and Development Environment
This is the funny part

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
