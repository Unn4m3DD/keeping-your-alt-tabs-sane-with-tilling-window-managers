# Arch Wiki is your best friend (even if you don't use arch (I use arch btw))
Arch wiki is arguably the best linux resource you'l ever find, it is community based and usually has lots of tips on the intricacies of the software so that you don't get lost in weird quirks for hours as it usually happens in open source stuff

## Window Manager (WM) vs Desktop Environments (DE)
Desktop environments are full blown desktop experiences, they include all the bells and whistles you might possibly need from a calculator app, a settings app, a sound management app, a terminal app, a lockscreen, an automated way to mount external block devices, maybe even some games (**cough gnome**...)  
A window manager on the other hands is not battery included, they allow for loads of customization and do spoon you features you don't explicitly want

# How to use i3

## Installing i3-gaps
To install i3-gaps we need to compile it from source since there is no apt package available with it
```sh
apt install dh-autoreconf libxcb-keysyms1-dev libpango1.0-dev libxcb-util0-dev xcb libxcb1-dev libxcb-icccm4-dev libyajl-dev libev-dev libxcb-xkb-dev libxcb-cursor-dev libxkbcommon-dev libxcb-xinerama0-dev libxkbcommon-x11-dev libstartup-notification0-dev libxcb-randr0-dev libxcb-xrm0 libxcb-xrm-dev libxcb-shape0 libxcb-shape0-dev

# clone the repository
git clone https://www.github.com/Airblader/i3 i3-gaps
cd i3-gaps

mkdir -p build && cd build
meson ..
ninja
sudo ninja install
```

## Installing dmenu
```sudo apt install dmenu```

## The \[mod\] key
The mod key is a key of your choice (usually the windows key) that you give up in order to control the i3. It is used on all the following features

## Moving between windows
Moving between windows can be made with the command `[mod] + [arrow keys]`

## Resizing windows
Resizing can be made with the command `[mod] + r` to ender resize mode and then using the `arrow keys` to resize in a particular direction. At the end of it you'l need to use `[mod] + r` again to return to normal mode
Alternatively, and according to some sacrilegiously, you can also hold `[mod]` and drag the windows with the right click

## Moving windows arroud
Moving windows can be made with the command `[mod] + shift + [arrow keys]` while focused on the window you want to move

## Creating floating windows
Creating a floating window can be made with `[mod] + shift + space` and you can return it to a normal window with the same command

## Multiple workspaces
On i3 there is the concept of multiple workspaces to organize your workflow, by default you can access them using the command `[mod] + [number 1 through 9]`

## Changing window direction
Changing the windows spawn direction can be made with the command `[mod] + e` this will toggle the current window context's direction from horizontal to vertical and vice versa

## How to achieve a Unix Porn visual
I'm sure you've seen time and time again the unix porn subreddit full of gorgeous environments. To achieve this you need nothing more than a couple of configuration lines on your i3 config file!

### Changing background with feh
We'l start by chaging the current background to something more fancy using a program called feh.  
To achieve this we can use the command `feh --bg-scale /path/to/image.file`  
After we make sure that the command works as intended we can save it to the i3 config file so that it runs at startup

### Configuring i3-gaps
Now we'l change the default configuration of i3 to something more palatable by creating gaps between windows and removing 2000s blue outline

# The pursuit for a Unix Porn environment continues!

## Setting up a status bar

### Installing polybar
You can install polybar directly from apt
```sh
sudo apt install polybar
```

### Configuring polybar
To configure polyar we'l be using a theme framework to make it easier to start messing around
To install it we can run the following commands
```sh
git clone --depth=1 https://github.com/adi1090x/polybar-themes.git
cd polybar-themes
chmod +x setup.sh
./setup.sh
```
To test different themes we can run
```sh
bash ~/.config/polybar/launch.sh
```

## Setting up your terminal app

### Instaling alacritty
To install alacritty again there is not prebuilt version for ubuntu so we'l install it via cargo
```sh
sudo apt install cargo -y
echo 'export PATH=$PATH:$HOME/.cargo/bin' >> ~/.bashrc
source ~/.bashrc
cargo install alacritty 
```
Then we can edit i3 config to use alacritty as its default terminal
```
bindsym $mod+Return exec /home/osboxes/.cargo/bin/alacritty
```

### Installing a nerd font 
To instal the Meslo font we'l use the following script 
```sh
sudo apt install fontconfig
cd ~
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/Meslo.zip
mkdir -p .local/share/fonts
unzip Meslo.zip -d .local/share/fonts
cd .local/share/fonts
rm *Windows*
cd ~
rm Meslo.zip
fc-cache -fv
``` 

At last we'l configre alacritty to use this font with the config
```yml
font:
    normal:
          family: MesloLGS Nerd Font
```

### Installing powerlevel10k

#### Installing zsh
To install zsh we'l run `sudo apt install zsh -y`
To enable it we need to run `chsh -s /usr/bin/zsh`

#### Installing oh my zsh
To install oh my zsh we'l run `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

#### Installing powerlevel10k
Finally to install powerlevel10 we run 
```sh 
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```
And to enable it we change the zsh configuration to use it as a theme by adding the following line to ~/.zshrc
```sh
ZSH_THEME="powerlevel10k/powerlevel10k"
```
Now we can customize pl10k with the command 
```sh
p10k configure
```

# Playing super tux and experiencing responsiveness
```sh
sudo apt install supertux
```
