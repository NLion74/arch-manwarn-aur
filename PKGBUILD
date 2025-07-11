# Maintainer: nlion <nlion@nlion.nl>
pkgname=arch-manwarn
pkgver=0.9.2
pkgrel=1
pkgdesc="Rust-based pacman hook that blocks updates if unread Arch News posts require manual intervention"
arch=('x86_64')
url="https://github.com/NLion74/arch-manwarn"
license=('UNLICENSE')
depends=('pacman' 'curl')
conflicts=('informant')
makedepends=('rust' 'cargo')
options=(!lto !debug)
source=("$pkgname-$pkgver.tar.gz::$url/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('8868a20e83e59fea40c5e97d8e6a885c9aedcf6194e542f8bcb8640e41a8c979')

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
  install -Dm644 "man/arch-manwarn.1" "$pkgdir/usr/share/man/man1/arch-manwarn.1"
}
