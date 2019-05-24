# Ly - a TUI display manager (for Void Linux)
[![CodeFactor](https://www.codefactor.io/repository/github/cylgom/ly/badge/master)](https://www.codefactor.io/repository/github/cylgom/ly/overview/master)
![ly screenshot](https://user-images.githubusercontent.com/5473047/42466218-8cb53d3c-83ae-11e8-8e53-bae3669f959c.png "ly on st")

Ly is a lightweight, TUI (ncurses-like) display manager for Linux.  

## Patches added in fork
- runit service instead of systemd one by @qub1750ul
- \* instead of O as a password mask
- it language patch by @termgod
- tab cycles between fields

## Dependencies
Make sure all the following packages are properly installed and configured
before going further:
- a C99 compiler (tested with gcc and tcc)
- a C standard library
- make
- linux-pam
- xorg
- xorg-xinit
- xorg-xauth
- mcookie
- tput
- shutdown

## Cloning and Compiling
This repository uses submodules, to clone it properly please use
```
git clone --recurse-submodules https://github.com/cylgom/ly.git
```

To compile you just need to launch make in the created folder
```
make
```

Check if it works on the tty you configured (default is tty2). You can
also run it in terminal emulators, but desktop environments won't start
```
sudo make run
```

Then, install Ly and the systemd service file
```
sudo make install
```

Now enable the runit service to make it spawn on startup
```
sudo ln -s /etc/sv/ly-runit-service /var/service/
```

You can disable getty-tty2
```
sudo rm /var/service/agetty-tty2
```

If messages from other services pop over the login prompt,
edit open the configuration and make sure `force_update` is enabled
```
[box_main]
force_update=1
```

## Configuration
All the configuration takes place in `/etc/ly/config.ini`.
The file is commented, and includes useful defaults.

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
I wish to thank linux-pam, X11 and systemd developers for not
providing anything close to a reference or documentation.
