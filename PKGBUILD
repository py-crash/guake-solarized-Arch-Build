# Maintainer: Agustin Ferrario 'py_crash' <agustin dot ferrario at hotmail dot com>

pkgname=guake-colors-solarized-git
pkgver=20130221
pkgrel=1
pkgdesc="Precision colors for machines and people. Guake integration"
arch=('any')
url="http://ethanschoonover.com/solarized"
license=('Custom, FOSS')
makedepends=('git')
depends=('guake')
provides=('guake-colors-solarized')
source=(dir.patch)
md5sums=('25f2b58cac3baf491eeb75b30ac6495a')
_gitroot="https://github.com/coolwanglu/guake-colors-solarized.git"
_gitname="guake-colors-solarized"

build() {
  # {{{ git
  
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  msg "GIT checkout done or server timeout."
  msg "Starting making package..."
  # }}}

}

package(){
    patch -p1 $_gitname-build/set_dark.sh < dir.patch
    patch -p1 $_gitname-build/set_light.sh < dir.patch
    cd "$srcdir/$_gitname-build"
    
    install -dm755 ${pkgdir}/usr/bin
    install -Dm755 set_dark.sh          ${pkgdir}/usr/bin/
    install -Dm755 set_light.sh         ${pkgdir}/usr/bin/
    
    install -dm755 ${pkgdir}/usr/share/guake/solarized-colors/
    mv colors/ ${pkgdir}/usr/share/guake/solarized-colors/              

    install -dm755 ${pkgdir}/usr/share/guake/solarized-colors/doc
    install -Dm644 README.mkd           ${pkgdir}/usr/share/guake/solarized-colors/doc
    
    install -dm755 ${pkgdir}/usr/share/licenses/guake-colors-solarized/
    install -Dm644 LICENSE.mkd          ${pkgdir}/usr/share/licenses/guake-colors-solarized/
}

