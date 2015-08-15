pkgname=go-glfw
pkgver=20120304
pkgrel=3
pkgdesc="Multi-platform OpenGL library, for Go"
arch=('x86_64' 'i686')
url="http://github.com/jteeuwen/glfw"
license=('custom:CC0')
depends=('go-opengl' 'glfw')
makedepends=('go' 'go-check')
options=('!strip' '!emptydirs')
_gourl=github.com/jteeuwen/glfw

build() {
  cd "$srcdir"
  GOPATH="$srcdir" go get -v -x ${_gourl}/...
}

check() {
  source /etc/profile.d/go.sh
  GOPATH="$GOPATH:$srcdir" go test -v -x ${_gourl}/...
}

package() {
  source /etc/profile.d/go.sh
  mkdir -p "${pkgdir}/$GOPATH"
  cp -Rv --preserve=timestamps ${srcdir}/{src,pkg} "${pkgdir}/$GOPATH"

  # Package license (if available)
  for f in LICENSE COPYING; do
    if [ -e "$srcdir/src/$_gourl/$f" ]; then
      install -Dm644 "$srcdir/src/$_gourl/$f" \
        "$pkgdir/usr/share/licenses/$pkgname/$f"
    fi
  done
}

# vim:set ts=2 sw=2 et:
