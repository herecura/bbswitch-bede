# Maintainer: Sven-Hendrik Haase <sh@lutzhaase.com>
# Contributor: M0Rf30
# Contributor: Samsagax <samsagax@gmail.com>

pkgname=bbswitch-bede
_basename=bbswitch
pkgver=0.8
_extramodules=5.2-BEDE-external
_current_linux_version=5.2.15
_next_linux_version=5.3
pkgrel=226
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
)
source=("${_basename}-$pkgver.tar.gz::https://github.com/Bumblebee-Project/bbswitch/archive/v${pkgver}.tar.gz")
sha512sums=('11ab163931feb6c0e202d04c4552b848e999fedea9990390c26b28abdb4a69081ccfb5a22d1e390cc274f1c0cfc9adedc719c5fece14738b17aaa93e28865b7c')

build() {
  cd ${srcdir}/${_basename}-${pkgver}

  _kernver="$(cat /usr/lib/modules/${_extramodules}/version)"

  make KDIR=/lib/modules/${_kernver}/build
}

package() {
  cd ${srcdir}/${_basename}-${pkgver}
   
  install -Dm644 bbswitch.ko "${pkgdir}"/usr/lib/modules/${_extramodules}/bbswitch.ko
  find "${pkgdir}" -name '*.ko' -exec xz {} +
}
