# Maintainer: Diego Pi
# Developer: Vincenzo Cimmelli
# Contributor: Umberto Reale

pkgname=tubeflush-git
pkgver=20130214
pkgrel=1
pkgdesc="A script to download music from YouTube videos"
arch=('i686' 'x86_64')
url="https://github.com/vencizon/tubeflush"
license=('GPL3')
makedepends=('git')
depends=('youtube-dl' 'ffmpeg' 'lame')
provides=("tubeflush=$pkgver")
conflicts=('tubeflush')

_gitroot="git://github.com/vencizon/tubeflush"
_gitname="tubeflush"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
}

package() {
  cd $srcdir/$_gitname
  install -Dm755 tubeflush $pkgdir/usr/bin/tubeflush
  install -Dm644 README.md $pkgdir/usr/share/$pkgname/README.md
}
