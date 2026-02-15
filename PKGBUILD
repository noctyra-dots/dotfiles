# Maintainer: <Cleboost> <clement.balarot@gmail.com>

pkgname=noctyra-dotfiles
pkgver=1.0.0
pkgrel=1
pkgdesc="Noctyra dotfiles (release) - stow packages installed system-wide"
arch=('any')
url="https://github.com/noctyra-dots/dotfiles"
license=('MIT')

depends=('stow')

source=("$pkgname-$pkgver.tar.gz::$url/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('SKIP')  # <- recommandé: remplace par le vrai hash

package() {
  install -d "$pkgdir/usr/share/noctyra"
  local srcdir_stow
  srcdir_stow="$(find "$srcdir" -maxdepth 3 -type d -name stow -print -quit)"

  if [[ -z "$srcdir_stow" ]]; then
    echo "ERROR: couldn't find 'stow/' directory in the source archive."
    echo "Make sure your release tarball contains: stow/<module>/.config/..."
    return 1
  fi

  cp -a "$srcdir_stow" "$pkgdir/usr/share/noctyra/stow"

#   local readme
#   readme="$(find "$srcdir" -maxdepth 3 -type f -iname README.md -print -quit || true)"
#   [[ -n "$readme" ]] && install -Dm644 "$readme" "$pkgdir/usr/share/noctyra/README.md"

#   local license
#   license="$(find "$srcdir" -maxdepth 3 -type f -iname LICENSE -print -quit || true)"
#   [[ -n "$license" ]] && install -Dm644 "$license" "$pkgdir/usr/share/noctyra/LICENSE"
}
