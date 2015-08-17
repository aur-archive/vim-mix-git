# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=vim-mix-git
pkgver=20130516
pkgrel=1
pkgdesc="Vim plugin for using Elixir's build tool, mix"
arch=('any')
depends=('vim')
makedepends=('git')
groups=('vim-plugins')
url="http://mattreduce.github.io/vim-mix/"
license=('custom:vim')
source=(${pkgname%-git}::git+https://github.com/mattreduce/vim-mix)
sha256sums=('SKIP')
provides=('vim-mix')
conflicts=('vim-mix')
install=vimdoc.install

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  cd ${pkgname%-git}

  msg 'Installing docs...'
  install -Dm 644 README.md "$pkgdir/usr/share/doc/vim-mix/README.md"
  install -Dm 644 CONTRIBUTING.md "$pkgdir/usr/share/doc/vim-mix/CONTRIBUTING.md"

  msg 'Installing dirs...'
  install -dm 755 "$pkgdir/usr/share/vim/vimfiles"
  for _dir in doc plugin; do
    cp -dpr --no-preserve=ownership $_dir "$pkgdir/usr/share/vim/vimfiles/$_dir"
  done

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
}
