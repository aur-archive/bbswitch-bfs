# Maintainer: Piotr Gorski <sir_lucjan@openlinux.pl>
# Contributor: Boyan Ding <stu_dby@126.com>

pkgname=bbswitch-bfs
pkgver=0.8
pkgrel=5
_realname=bbswitch
_extramodules=extramodules-3.18-bfs 
pkgdesc="Kernel module allowing to switch dedicated graphics card on Optimus laptops for linux-bfs"
arch=('i686' 'x86_64')
url=("http://github.com/Bumblebee-Project/bbswitch")
license=('GPL')
depends=('linux-bfs>=3.18' 'linux-bfs<3.19')
makedepends=('linux-bfs-headers>=3.18' 'linux-bfs-headers<3.19')
install=bbswitch-bfs.install
source=("https://github.com/Bumblebee-Project/bbswitch/archive/v${pkgver}.tar.gz")
md5sums=('5b116b31ace3604ddf9d1fc1f4bc5807')

build() {
  cd ${srcdir}/${_realname}-${pkgver}

  _kernver="$(cat /usr/lib/modules/${_extramodules}/version)"

  make KDIR=/lib/modules/${_kernver}/build
}

package() {
  cd ${srcdir}/${_realname}-${pkgver}
   
  install -Dm644 bbswitch.ko "${pkgdir}"/usr/lib/modules/${_extramodules}/bbswitch.ko
  gzip "${pkgdir}/usr/lib/modules/${_extramodules}/bbswitch.ko"                      
}
