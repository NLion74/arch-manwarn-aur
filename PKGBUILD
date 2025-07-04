# Maintainer: Your Name <your@email.com>
pkgname=arch-manwarn
pkgver=0.5.0
pkgrel=1
pkgdesc="arch-manwarn is a minimalist utility written in Rust that checks the Arch news RSS feed for manual intervention warnings and blocks your pacman upgrade or install if action is needed."
arch=('x86_64')
url="https://github.com/NLion74/arch-manwarn"
license=('UNLICENSE')
depends=('pacman' 'curl')
makedepends=('rust' 'cargo')
source=("$pkgname-$pkgver.tar.gz::$url/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('4118c2b9108d6b6601f7ecf1ab73e2b01497eacd995e008728e5ae52fde1dcb7')

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
