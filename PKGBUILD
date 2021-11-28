# Maintainer:Antonio Rojas <arojas@archlinux.org>

pkgname=plasma-pa-git
pkgver=5.20.90
pkgrel=1
pkgdesc='Plasma applet for audio volume management using PulseAudio'
arch=(x86_64)
url='https://kde.org/plasma-desktop/'
license=(LGPL)
depends=(plasma-workspace-git libcanberra-pulse pulseaudio perl)
makedepends=(extra-cmake-modules-git kdoctools-git)
groups=(plasma)
provides=('plasma-volume-control' 'plasma-pa')
conflicts=('plasma-volume-control' 'plasma-volume-control-git' 'plasma-pa')
source=('git+https://invent.kde.org/plasma/plasma-pa.git')
md5sums=('SKIP')

pkgver() {
  cd plasma-pa
  _ver="$(cat CMakeLists.txt | grep -m1 'set(PROJECT_VERSION' | cut -d '"' -f2 | tr - .)"
  echo "${_ver}.r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S plasma-pa \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}