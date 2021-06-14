license=('MIT')
arch=('x86_64')
pkgname=cjson
pkgver=1.7.14
pkgrel=1
pkgdesc="Ultralightweight JSON parser in ANSI C"
makedepends=('cmake')
url="https://github.com/DaveGamble/cJSON"
source=("$pkgname-$pkgver.tar.gz::https://github.com/DaveGamble/cJSON/archive/v$pkgver.tar.gz")
sha512sums=('8de1dedc123ed025a9cbe6764e5963eb0550f726d06a8f6bedfe05b84e852cd9c1587cd381669663073967f42be894a535ba239013f304ce544c3b15a6477c01')

build() {
  cmake -B build -S "cJSON-${pkgver}" \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DENABLE_CJSON_UTILS=On
  make -C build
}

check() {
  make -C build check
}

package() {
  make -C build DESTDIR="${pkgdir}" install
  install -Dm644 "$srcdir/cJSON-$pkgver/LICENSE" \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
