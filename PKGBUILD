# Maintainer: DavidK <david_king at softhome dot net>

pkgname=cl-ssl-git
_clname=cl+ssl
pkgver=r100.65c360d
pkgrel=2
pkgdesc="A Common Lisp interface to OpenSSL"
arch=('any')
url="http://common-lisp.net/project/cl-plus-ssl/"
license=('BSD')
provides=('cl-ssl')
depends=('common-lisp' 'cl-alexandria' 'cl-babel' 'cl-cffi' 'cl-flexi-streams' 'cl-trivial-features' 'cl-trivial-gray-streams')
makedepends=('git')
optdepends=('cl-trivial-sockets: For the test suite')
install=cl-ssl.install
source=("$pkgname"::'git+https://github.com/cl-plus-ssl/cl-plus-ssl')
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
  install -d "${pkgdir}"/usr/share/common-lisp/source/${_clname}
  install -d "${pkgdir}"/usr/share/common-lisp/systems
  install -d "${pkgdir}"/usr/share/licenses/${pkgname}

  cd "${srcdir}/$pkgname"

  install -m 644 -t "${pkgdir}"/usr/share/common-lisp/source/${_clname} \
    *.lisp || return 1
  install -m 644 -t "${pkgdir}"/usr/share/common-lisp/source/${_clname} \
    *.asd || return 1
  install -m 644 LICENSE "${pkgdir}"/usr/share/licenses/${pkgname} || return 1

  cd "${pkgdir}"/usr/share/common-lisp/systems
  ln -s ../source/${_clname}/${_clname}.asd .
}

# vim:set ts=2 sw=4 et nospell:
