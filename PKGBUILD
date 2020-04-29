# vim:set ft=sh et:
# Maintainer: Sven-Hendrik Haase <sh@lutzhaase.com>
# Contributor: M0Rf30
# Contributor: Samsagax <samsagax@gmail.com>

_pkgname=bbswitch
pkgname=$_pkgname-bede
pkgver=0.8
_current_linux_version=5.6.8
_next_linux_version=5.7
pkgrel=290
pkgdesc="Kernel module allowing to switch dedicated graphics card on Optimus laptops"
arch=('x86_64')
url="http://github.com/Bumblebee-Project/bbswitch"
license=('GPL')
depends=(
    "linux-bede>=$_current_linux_version"
    "linux-bede<$_next_linux_version"
)
makedepends=(
    "linux-bede-headers>=$_current_linux_version"
    "linux-bede-headers<$_next_linux_version"
    "bbswitch-dkms>=$pkgver"
)
source=()


package() {
    local kernver=$(</usr/src/linux-bede/version)
    local extradir="/usr/lib/modules/$kernver/extramodules"
    install -dm755 "${pkgdir}${extradir}/$_pkgname"
    cp -a "/var/lib/dkms/$_pkgname/kernel-$kernver-x86_64/module"/* \
        "${pkgdir}${extradir}/$_pkgname/"
}










