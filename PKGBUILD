# Maintainer: Brennan Tracy <brennantracy4@gmail.com>

pkgname="BrongBot"
pkgver=r3.ea02550
pkgrel=1
pkgdesc="A bot to control my AWS account"
arch=("any")
license=("MIT")
depends=("python3")
makedepends=("git")
source=("$pkgname::git+https://github.com/HBBrennan/$pkgname.git")
sha256sums=('SKIP')

pkgver() {
    cd "$pkgname"
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
    cd "$pkgname"
    python setup.py build
}

package() {
      cd "$pkgname"
    python setup.py install --root="$pkgdir" --optimize=1 --skip-build
}

