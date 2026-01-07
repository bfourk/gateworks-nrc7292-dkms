# DKMS module for both Gateworks' ftdi-usb-spi driver and nrc7292 driver.
* Tested on Arch Linux 6.18.3-arch1-2, but it should work on 6.18+
* Original driver source + credit is linked in individual driver's README files (in nrc and ftdi-usb-spi)

### Notes
* The driver requires that a regulatory domain is set before functioning. On Arch, this requires having `wireless-regdb` installed and setting your regulatory domain via. `iw reg set US`, with US being your specific domain.
* The NRC driver requires certain arguments to function properly, notably `bd_name` and `spi_gpio_irq`. This is automatically taken care of in the Arch package
* The card can be used with NetworkManager and NetworkManager's nmcli-applet
* There is a PKGBUILD given to automatically build and install DKMS drivers for you.
* The driver appears to throw some kind of panic/oops/warning when setting the regulatory domain for the first time with a card installed, but it doesn't crash my system and the driver+card still work.

## Building/Installing
1. Clone the repository `git clone https://github.com/bfourk/gateworks-nrc7292-dkms` 
2. CD into the repositories' main folder
3. Run `makepkg -si`