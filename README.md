# Deezer Solus build script

![Deezer](https://preview.redd.it/us86nuehruc51.png?width=1920&format=png&auto=webp&s=ef48b4aa0c98a4d0e0d869282a10e93127f9e927)

Unofficial script to install Deezer desktop on Solus. Based on [the AUR Script by SibrenVasse](https://aur.archlinux.org/packages/deezer/).

For Windows, Deezer distributes a version of the Electron run time (Windows binary) and the source code of their application itself. The build process of this package extracts the application source from the Windows installer.

This package applies several patches for:

- Compatibility with newer Electron versions
- Compatibility with a Linux environment in general.
- Fixing bugs

## Building

To install on Solus:

```bash
git clone https://github.com/ressonix/deezer
cd deezer
chmod +x ./install.sh
./install.sh
```

The Deezer Windows installer will then be downloaded, extracted and patched to work for Linux. When prompted for your sudo password, please enter it.

## Debugging

Running the application from the command line will show verbose logging.

```bash
deezer
```

To run the application with devtools by running

```bash
env DZ_DEVTOOLS=yes electron /usr/share/deezer/app.asar
```

To debug node, you can extract the source files to a directory and inspect the node process by attaching using the chromium debugging tools. (<https://www.electronjs.org/docs/tutorial/debugging-main-process>)

```bash
asar extract /usr/share/deezer/app.asar $dest
electron --inspect-brk=$port $dest
```
