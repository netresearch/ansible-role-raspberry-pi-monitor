# Ansible role for Raspberry Pi monitoring kiosk

This role provides a basic setup for Raspberry Pi monitor (kiosk mode).

## Requirements

* Ansible >= 2.7
* Raspbian Stretch with Desktop

## Setting up a Raspberry Pi

 1. Download the image "Raspbian Stretch with Desktop" from `https://www.raspberrypi.org/downloads/raspbian/`.
 2. Unzip the .zip file which contains the image with `The Unarchiver (Mac) or Unzip (Linux)`.
 3. Download Etcher from `https://www.balena.io/etcher/` and install it.
 4. Connect an SD card reader with the SD card inside.
 5. Open Etcher and select from your hard drive the Raspberry Pi .img file you wish to write to the SD card.
 6. Select the SD card you wish to write your image to.
 7. Review your selections and click 'Flash!' to begin writing data to the SD card.
 8. Open a terminal, change into the boot directory of the µSD-card and execute `sudo touch ssh`.
 9. Put the µSD-card into the Pi and plug in the µ-USB-cable for power.
10. `Enjoy!`

## Variables

| variable   | description             | default               |
| ---------- | ----------------- | --------------------- |
| pi_user_name | Default desktop user | `"pi"` |
| pi_user_group | Primary group of default desktop user | `"pi"` |
| chromium_url | The URL to open in kiosk mode | `"https://www.youtube.com/"` |
| chromium_scale_factor | Device scale factor | `"1.0"` |
| chromium_windowname | Chromium window title | `"YouTube - Chromium"` |

## Example playbook

```yaml
- name: Configure raspberry pi as monitoring kiosk
  hosts: localhost
  tasks:
    - name: Configure monitoring kiosk
      include_role:
        name: raspberry-pi-monitor
      vars:
        chromium_url: "https://www.youtube.com/"
```
