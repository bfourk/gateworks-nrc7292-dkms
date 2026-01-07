pkgname=nrc-ft232h-dkms
pkgver=1.0
pkgrel=1
pkgdesc="DKMS modules, blobs, and configs for Gateworks' FT232H SPI driver and NRC7292 driver"
arch=('any')
license=('GPL2')
depends=('dkms' 'linux-headers')
source=()
md5sums=()


package() {
    cd "$srcdir/.."

    # FT232H module
    install -d "$pkgdir/usr/src/gw-ft232h-$pkgver"
    cp -r gw-ft232h/* "$pkgdir/usr/src/gw-ft232h-$pkgver"

    # NRC7292 module
    install -d "$pkgdir/usr/src/gw-nrc7292-$pkgver"
    cp -r gw-nrc7292/* "$pkgdir/usr/src/gw-nrc7292-$pkgver"

    # Add blobs
    install -d "$pkgdir/usr/lib/firmware/nrc"
    install -m644 blobs/nrc7292_bd.dat "$pkgdir/usr/lib/firmware/nrc/"
    install -m644 blobs/nrc7292_cspi.bin "$pkgdir/usr/lib/firmware/nrc/"

    # Add NRC modprobe config
    install -d "$pkgdir/etc/modprobe.d"
    install -m644 nrc.conf "$pkgdir/etc/modprobe.d/"
}

post_install() {
    dkms install gw-ft232h/$pkgver
    dkms install gw-nrc7292/$pkgver
}

post_upgrade() {
    dkms install gw-ft232h/$pkgver
    dkms install gw-nrc7292/$pkgver
}

pre_remove() {
    dkms remove gw-ft232h/$pkgver --all
    dkms remove gw-nrc7292/$pkgver --all
}