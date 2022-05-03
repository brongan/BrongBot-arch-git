# Maintainer: Brennan Tracy <brennantracy4@gmail.com>

pkgname="BrongBot"
pkgver=r5.8763189
pkgrel=1
pkgdesc="A bot to control my AWS account"
arch=("any")
license=("MIT")
depends=("python3" "python-discord" "python-boto3")
makedepends=("git" "python-setuptools")
backup=("etc/sysconfig/brong_botd/aws_environment")
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
    install -Dm644 service/brong_botd.service -t "$pkgdir/usr/lib/systemd/system"
    install -Dm644 LICENSE -t "$pkgdir/usr/share/licenses/$pkgname"
    install -DM644 README.md -t "$pkgdir/usr/share/$pkgname"
    install -Dm600 service/aws_environment.default -T "$pkgdir/etc/sysconfig/brong_botd/aws_environment.example"
}

