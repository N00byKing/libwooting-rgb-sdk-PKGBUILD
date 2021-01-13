_gitname=wooting-rgb-sdk
pkgname="libwooting-rgb-sdk-git"
url='https://github.com/WootingKb/wooting-rgb-sdk'
arch=("x86_64")
pkgver=5c9975b
pkgrel=1
pkgdesc="Wooting Keyboard RGB SDK"
provides=('libwooting-rgb-sdk')
conflicts=('libwooting-rgb-sdk')
depends=('libusb')
makedepends=('git' 'hidapi' 'libusb')
license=('MPL2')
source=('git+https://github.com/N00byKing/wooting-rgb-sdk')
md5sums=(SKIP)

pkgver() {
    cd "$_gitname"
    git rev-parse --short HEAD
}

build() {
    cd "$srcdir/$_gitname"
    git submodule update --init
    cd linux
    CFLAGS+=" -fPIC" make
}

package() {
    cd "$srcdir/$_gitname/linux"
    install -Dm755 libwooting-rgb-sdk.so "$pkgdir/usr/lib/libwooting-rgb-sdk.so"
    sed "s/VERSION/${pkgver}/" -i libwooting-rgb-sdk.pc
    install -Dm644 libwooting-rgb-sdk.pc "${pkgdir}/usr/lib/pkgconfig/libwooting-rgb-sdk.pc"
    cd "$srcdir/$_gitname/src"
    install -Dm755 wooting-rgb-sdk.h "$pkgdir/usr/include/wooting-rgb-sdk.h"
}
