# dwm - Dynamic Window Manager

An extremely fast, small, and dynamic window manager for X, with modifications by Andrew in 2024.

## Overview

`dwm` is designed to be simple yet powerful, adhering to the **suckless philosophy** of minimalism and efficiency. It allows dynamic window management with a focus on usability and performance.

Andrew's 2024 modifications add enhanced key bindings and support for sound management via `alsamixer`, while preserving the core functionality of `dwm`.

## Requirements

To build and run `dwm`, ensure the following dependencies are installed:

- **Xlib header files**: Required for building `dwm`.
- **[scripts-control](https://github.com/AndrewXZR/scripts-control)**: A separate repository containing custom scripts for managing sound, brightness, and touchpad toggling.
- **alsamixer**: required to modify the sound status by raising, lowering and muting.
- **flameshot**: required to take screenshots when pressing print screen key.
- **qalculate-gtk**: required for the default calculator associated with a key.

## Installation

1. Edit `config.mk` to suit your local setup. By default, `dwm` is installed into the `/usr/local` namespace.

2. Build and install `dwm` by running the following commands:

    ```bash
    make clean install
    ```

   If root privileges are required for installation, use `sudo` or switch to the root user.

## Running dwm

To start `dwm` using `startx`, add the following line to your `.xinitrc` file:

```bash
exec dwm
```
To run dwm on a specific display, ensure the DISPLAY environment variable is set correctly. For example:

```bash
DISPLAY=foo.bar:1 exec dwm
```
This will start `dwm` on display :1 of the host foo.bar.

Status Bar Configuration
To display status information in the bar, add a loop like the following to your .xinitrc:
```bash
while xsetroot -name "`date` `uptime | sed 's/.*,//'`"
do
    sleep 1
done &
exec dwm
```

## Keybindings

- **Sound Management:**
  - **Increase Volume:** Press `XF86AudioRaiseVolume` to raise the system volume.
  - **Decrease Volume:** Press `XF86AudioLowerVolume` to lower the system volume.
  - **Mute/Unmute:** Press `XF86AudioMute` to toggle mute on or off.
  These keybindings utilize `alsamixer` and custom scripts from the [scripts-control](https://github.com/AndrewXZR/scripts-control) repository.

- **Brightness Adjustment:**
  - **Increase Brightness:** Press `XF86MonBrightnessUp` to increase screen brightness.
  - **Decrease Brightness:** Press `XF86MonBrightnessDown` to decrease screen brightness.
  This functionality requires a compatible script from the `scripts-control` repository.

- **Touchpad Toggle:** Press `XF86TouchpadToggle` to enable or disable the touchpad.
  This relies on a script included in the `scripts-control` repository.

- **Screenshot:** Press the `PrintScreen` key to capture a screenshot using `flameshot`.
  Ensure `flameshot` is installed and configured for this feature.


- **Calculator:** Press the `XF86Calculator` key to launch the calculator application.
  By default, this keybinding launches `qalculate-gtk`. You can modify this behavior in `config.h` by specifying a different application.

## Configuration
`dwm` is configured by modifying the source code. Create a custom config.h file with your desired settings and recompile dwm to apply the changes.

## License
`dwm` is distributed under the MIT/X Consortium License.

Andrew's modifications in 2024 comply with the original licensing terms, maintaining the same license. For more information on the original dwm, visit suckless.org.