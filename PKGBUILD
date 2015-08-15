# Maintainer: Dmitry Lavnikevich <haff@midgard.by>

pkgname=extopts
pkgver=2.0.0
pkgrel=1
pkgdesc="Command line interface library"
url="https://github.com/githaff/extopts"
license=('BSD')
arch=('i686' 'x86_64')
makedepends=('git' 'cmake')

_gitroot="git://github.com/githaff/extopts.git"
_gitname="extopts"

dirname=${_gitname}-${pkgver}

build() {
  msg "Connecting to GIT server..."

  if [ -d $_gitname ] ; then
    cd ${dirname} && git pull origin v${pkgver}
    git checkout v${pkgver}
    msg "The local files are updated."
  else
    git clone ${_gitroot} ${dirname}
    cd ${dirname}
    git checkout -q v$pkgver
  fi

  msg "Configuring..."
  cmake \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release

  msg "Compiling..."
  make
}

package(){
  cd ${_gitname}-${pkgver}
  make DESTDIR="${pkgdir}/" install
}
