# Ly - a TUI display manager (for Artix Linux)
![Ly screenshot](https://user-images.githubusercontent.com/5473047/42466218-8cb53d3c-83ae-11e8-8e53-bae3669f959c.png "Ly screenshot")

Ly is a lightweight TUI (ncurses-like) display manager for Linux and BSD.

## Patches added in fork
- runit service instead of systemd one by @qub1750ul
- it language patch by @termgod
- service installed on default artix service path (/etc/runit/sv/)
- xsetup.sh is from the original ly by @nullgemm not from ly-void by @drozdowsky

## Dependencies
 - a C99 compiler (tested with tcc and gcc)
 - a C standard library
 - make
 - pam
 - xcb
 - xorg
 - xorg-xauth
 - mcookie
 - tput
 - shutdown

## Support
The following desktop environments were tested with success
 - budgie
 - cinnamon
 - deepin
 - enlightenment
 - gnome
 - i3
 - kde
 - lxde
 - lxqt
 - mate
 - sway
 - xfce
 - pantheon

Ly should work with any X desktop environment, and provides
basic wayland support (sway works very well, for example).

## systemd?
Unlike what you may have heard, Ly does not require `systemd`,
and was even specifically designed not to depend on `logind`.
You should be able to make it work easily with a better init,
changing the source code won't be necessary :)

## Cloning and Compiling
Clone the repository
```
git clone https://github.com/chaeold/ly-artix.git
```

Fetch submodules
```
make github
```

Compile
```
make
```

Install Ly and the provided systemd service file
Then, install Ly and the runit service file
```
sudo make install
```

Now enable the runit service to make it spawn on startup
```
sudo ln -s /etc/runit/sv/ly-runit-service/ /run/runit/service/
```

You can disable getty-tty2
```
sudo unlink /run/runit/service/agetty-tty2
```

## Configuration
You can find all the configuration in `/etc/ly/config.ini`.
The file is commented, and includes the default values.

## Controls
Use the up and down arrow keys to change the current field, and the
left and right arrow keys to change the target desktop environment
while on the desktop field (above the login field).

## Tips
The numlock and capslock state is printed in the top-right corner.
Use the F1 and F2 keys to respectively shutdown and reboot.
Take a look at your .xsession if X doesn't start, as it can interfere
(this file is launched with X to configure the display properly).

## Additional Information
The name "Ly" is a tribute to the fairy from the game Rayman.
Ly was tested by oxodao, who is some seriously awesome dude.
ly-artix tested by me, let me know if there's any issue.
