# dots

This is my personal configuration currently under void linux. 

## System

### Repositories (nonfree and multilib)
```bash
sudo xbps-install -Su
sudo xbps-install -Sy void-repo-nonfree
sudo xbps-install -Sy void-repo-multilib-nonfree
sudo xbps-install -Sy void-repo-multilib
```

### Packages

```bash
sudo xbps-install -S git pulseaudio alsa-plugins-pulseaudio xtools
```

### Install xbps-src

```bash
git clone https://github.com/void-linux/void-packages.git
cd void-packages
./xbps-src binary-bootstrap
echo XBPS_ALLOW_RESTRICTED=yes >> etc/conf
```

### Fonts

#### Install Microsoft Fonts

```bash
./xbps-src pkg msttcorefonts
xbps-install -R hostdir/binpkgs/nonfree msttcorefonts 
```

#### Disable Bitmap-Fonts

```bash
sudo ln -s /usr/share/fontconfig/conf.avail/70-no-bitmaps.conf /etc/fonts/conf.d/70-no-bitmaps.conf 
```

## Terminal

### Nushell

```bash
sudo xbps-install -S nushell
chsh -s /usr/bin/nu USERNAME
nu
```

```nushell
echo "let-env EDITOR = hx" | save -a $nu.env-path
```

### New Era tools

```nushell
sudo xbps-install -S helix bat bottom
```

### Aliases

```nushell
echo "alias ll = ls -al" | save -a $nu.config-path
```

## Gaming

### NVIDIA drivers

```nushell
sudo xbps-install -S nvidia nvidia-settings nvidia-libs-32bit
```

### Steam

```nushell
sudo xbps-install -S steam libgcc-32bit libstdc++-32bit libdrm-32bit libglvnd-32bit gamemode
```

#### Tweaks for Counter-Strike: Global Offensive

##### Disabling panorama background
Otherwise CS:GO will crash randomly on startup.

```nushell
cd `.steam/steam/steamapps/common/Counter-Strike Global Offensive/csgo/panorama/`
mv ./videos ./videos.bak
```

##### Launch options
Gamemode improves the performance drastically.

```
gamemoderun %command% -novid -nojoy
```
