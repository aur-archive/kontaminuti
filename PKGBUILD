# Maintainer: vicky91 <vickypaiers@gmail.com>
pkgname=kontaminuti
pkgver=20120131
pkgrel=1
pkgdesc="A simple helper utility to time your activities according to the Pomodoro Technique."
arch=('i686' 'x86_64')
url="https://projects.kde.org/projects/playground/utils/kontaminuti"
license=('GPL')
depends=('kdebase-runtime')
makedepends=('cmake' 'automoc4' 'git')
install=kontaminuti.install


_gitroot='git://anongit.kde.org/kontaminuti'
_gitname='kontaminuti'

build() {
  cd "${srcdir}"
  msg "Connecting to GIT server...."

  if [[ -d "${_gitname}" ]]; then
    cd "${_gitname}" && git pull origin
    msg "The local files are updated."
  else
    git clone "${_gitroot}" "${_gitname}"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "${srcdir}/${_gitname}-build"
  git clone "${srcdir}/${_gitname}" "${srcdir}/${_gitname}-build"
  cd "${srcdir}/${_gitname}-build"

  cmake . -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd "${srcdir}/${_gitname}-build"
  make DESTDIR="${pkgdir}/" install
}

# vim:set ts=2 sw=2 et:

