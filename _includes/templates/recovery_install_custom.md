{% case site.data.devices[page.device].unlock_bootloader_method[0] %}
{% when 'custom' %}
## Unlocking your bootloader

1. Unlock your bootloader by following [this]({{ site.data.devices[page.device].unlock_bootloader_method[1] }}) guide.
{% endcase %}

## Installing a custom recovery using `fastboot`

{% case site.data.devices[page.device].twrp_source[0] %}
{% when 'custom' %}
1. Download recovery - click [here]({{ site.data.devices[page.device].twrp_source[1] }}) to obtain the latest version of Team Win Recovery Project for your device.
{% when 'official' %}
1. Download recovery - visit [twrp.me](https://twrp.me/Devices/) to obtain the latest version of Team Win Recovery Project for your device.
{% endcase %}
2. Connect your device to your PC via USB.
3. Open a terminal on the PC and boot the device to fastboot mode by typing:

        adb reboot bootloader

    {% if site.data.devices[page.device].download_boot %}
    You can also boot into fastboot mode via a key combination:
    
    * {{ site.data.devices[page.device].download_boot }}
    {% endif %}
4. Once the device is in fastboot mode, verify your PC finds it by typing:

        fastboot devices

    If you see `no permissions fastboot` or `<waiting for device>`, try running `fastboot` as root/Administrator.
5. Flash recovery onto your device:

        fastboot flash recovery your_recovery_img.img

6. Now reboot into recovery to verify the installation:
    * {{ site.data.devices[page.device].recovery_boot }}
