# Maintainer: Your Name <your@email.com>
pkgname=arch-manwarn
pkgver=0.4.0
pkgrel=1
pkgdesc="Minimalist pacman hook to warn about Arch News manual interventions"
arch=('x86_64')
url="https://github.com/NLion74/arch-manwarn"
license=('UNLICENSE')
depends=('pacman' 'curl')
makedepends=('rust' 'cargo')
source=("$pkgname-$pkgver.tar.gz::$url/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('97854ba98ae2c9ce15e5b66d770f5341a9b09dab0b595afe59eaec8eba9e1e07')

build() {
  cd "$srcdir/$pkgname-$pkgver"
  cargo build --release --locked
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  install -Dm755 "target/release/arch-manwarn" "$pkgdir/usr/bin/arch-manwarn"
  install -Dm644 "hooks/arch-manwarn.hook" "$pkgdir/usr/share/libalpm/hooks/arch-manwarn.hook"
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -Dm644 README.md "$pkgdir/usr/share/doc/$pkgname/README.md"
}
