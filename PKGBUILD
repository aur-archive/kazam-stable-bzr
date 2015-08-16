# Contributor: myswiat <my.swiat AT o2 DOT pl>
pkgname=kazam-stable-bzr
pkgver=111
pkgrel=1
pkgdesc="A screencasting program with design in mind"
arch=('i686' 'x86_64')
url="https://launchpad.net/kazam"
license=('GPL')
groups=()
conflicts=('kazam-bzr' 'kazam')
depends=('pycairo' 'pygtk' 'ffmpeg' 'gstreamer0.10' 'pyxdg' 'python-xlib' 'libmatroska' 'gnome-python-desktop' 'python-pycurl' 'python-gdata' 'libtheora' 'python-keybinder')
makedepends=('bzr' 'python-distutils-extra')

install=
source=()

_bzrtrunk="lp:kazam"
_bzrmod="stable"

build() {
  cd "$srcdir"
  msg "Connecting to Bazaar server...."

  if [ -d $_bzrmod ] ; then
    cd $_bzrmod && bzr merge
    msg "The local files are updated."
  else
    bzr branch $_bzrtrunk/$_bzrmod
  fi

  msg "Bazaar checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_bzrmod-build"
  cp -r "$srcdir/$_bzrmod" "$srcdir/$_bzrmod-build"
  cd "$srcdir/$_bzrmod-build"

  python2 setup.py build
}

package() {
  cd "$srcdir/$_bzrmod-build"
  python2 setup.py install --root $pkgdir
}

