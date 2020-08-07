# vim:set ft=sh et:
# Maintainer: Sven-Hendrik Haase <sh@lutzhaase.com>
# Contributor: M0Rf30
# Contributor: Samsagax <samsagax@gmail.com>

_pkgname=bbswitch
pkgname=$_pkgname-bede
pkgver=0.8
_current_linux_version=5.7.14
_next_linux_version=5.8
pkgrel=316
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
source=('kernel-5.7.patch')
sha512sums=('5f9ac04b6a8552a406e808f86c5740062af56fdb4b37eab4b962933b43d53150120fda3c20dfe974494cdcd7394fd4856010eeb09852d6dabb8c859f6b9d8f7c')

## in case we need to do some patching
#build() {
    #_kernver="$(cat /usr/src/linux-bede/version)"

    ## dkms need modification to be run as user
    #cp -Lr /var/lib/dkms .
    #echo "dkms_tree='$srcdir/dkms'" > dkms.conf

    #(
        #cd dkms/$_pkgname/${pkgver}/source
        #patch -p1 -i "$srcdir/kernel-5.7.patch"
    #)
    ## build host modules
    #dkms --dkmsframework dkms.conf build "$_pkgname/${pkgver}" -k "$_kernver"
#}

package() {
    local kernver=$(</usr/src/linux-bede/version)
    local extradir="/usr/lib/modules/$kernver/extramodules"
    install -dm755 "${pkgdir}${extradir}/$_pkgname"
    # global dkms
    cp -a "/var/lib/dkms/$_pkgname/kernel-$kernver-x86_64/module"/* \
        "${pkgdir}${extradir}/$_pkgname/"
    # local home dkms
    #cp -a "$srcdir/dkms/$_pkgname/$pkgver/$kernver/x86_64/module"/* \
        #"${pkgdir}${extradir}/$_pkgname/"
}
