# Installing Visual Studio Code (VSCode) on Manjaro linux

Browse this link: http://umaranis.com/2018/07/05/installing-visual-studio-code-vscode-on-manjaro-linux/

## Install from "Add/Remove Software"

After enabling "AUR" repository in "Add/Remove Software" app, search for "visual-studio-code-bin". select "visual-studio-code-bin" from the list and click "Install".

## Install from AUR (Method # 1)

1. Acquire build files from Arch Linux user repository.
```
curl -L -O https://aur.archlinux.org/cgit/aur.git/snapshot/visual-studio-code-bin.tar.gz
```
2. Extract the downloaded package
```
tar -xvf visual-studio-code-bin.tar.gz
```
3. Change directory to the extracted package
```
cd visual-studio-code-bin
```
4. Build and install the package
```
makepkg -si
```

## Method 2 out of date! Checked at December 2023!!!
Not up to date! Check the Link via Browser from Method 2
```
http://repo.archlinux.fr
```
Checked at December 2023

418 - Gone

repo.archlinux.fr started in 2006, to host packages created by the Archlinux french community, with AFUR "Arch French User Repository".

The most famous package hosted was Yaourt, loved and hated by the community. 

Yaourt has been discontinued in 2018 (https://github.com/archlinuxfr/yaourt/issues/382), and nobody really uses repo.archlinux.fr anymore, so it's time to say goodbye (https://forums.archlinux.fr/viewtopic.php?t=22683, in french).

Enjoy,

Skunnyk,
Sept 2023


## Install using Yaourt (Method # 2)

It will be a two-step process. First, we will install Yaourt, then use it to install VS Code.

### Installing Yaourt

Edit Pacman configuration file to include the repository for Yaourt
```
sudo nano /etc/pacman.conf
```
Add the following lines at the end of the file and save it
```
[archlinuxfr]
SigLevel = Never
Server = http://repo.archlinux.fr/$arch
```
Now refresh the repository database and install Yaourt
```
sudo pacman -Sy yaourt
Installing VS Code
```
Yaourt makes installing VS Code pretty easy, we just have to execute the following command.
```
sudo yaourt visual-studio-code-bin
```

### Increasing NOFILE limit

During installation, you might get an error due to the limit on the number of files opened by a process.
To check the limit, use the following command:
```
$ ulimit -n
```
To increase the limit, add the following lines to /etc/security/limits.conf file.
```
<username>    soft    nofile  10000
<username>    hard    nofile  10000
```
Don’t forget to replace <username> with the logged in user’s name and also restart the machine for the change to take effort.
Links
