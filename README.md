## Tools to deal with daily Debian annoyances
Here are a collection of tools to address common daily linux frustrations.
Long file names are used so they are self-explanatory.
Read the comments within the files regarding usage

## Freshly minted user from the installer cannot sudo
```
su - root -c "adduser $USER sudo"
```

## `apt update` does not work out of the box
```
sudo sed -i'.bak' '/cdrom:/d' /etc/apt/sources.list
```

## `sudo_users_no_password_for_power_operations.rules`
Cinnamon on Debian prompts for passwords on shutdown/reboot/suspend after installing xrdp.
I expect it'd be the same for other Desktop Environment that uses Freedesktop (like GNOME).

Copy this file to `/usr/share/polkit-1/rules.d`
```
wget https://raw.githubusercontent.com/wonghoi/debian_annoyances/refs/heads/main/sudo_users_no_password_for_power_operations.rules -O /usr/share/polkit-1/rules.dsudo_users_no_password_for_power_operations.rules
```
and it will stop asking. Right now I only granted the convenience to `sudo` users. Feel free to modify the Javascript hook to your liking

