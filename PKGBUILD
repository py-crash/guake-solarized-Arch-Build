# Maintainer: Agustin Ferrario 'py_crash' <agustin dot ferrario at hotmail dot com>

pkgname=guake-colors-solarized-git
pkgver=20130211
pkgrel=1
pkgdesc="Precision colors for machines and people. Guake integration"
arch=('any')
url="http://ethanschoonover.com/solarized"
license=('Custom, FOSS')
makedepends=('git')
depends=('guake')
provides=('guake-colors-solarized')

_gitroot="https://github.com/coolwanglu/guake-colors-solarized.git"
_gitname="guake-colors-solarized"

##TODO patch, install dirs

build() {
    # {{{ git
    cd $srcdir

    msg "Connecting to GIT server..."
    if [ -d $_gitname ]; then
        cd $_gitname && git pull origin
        msg "The local files are updated."
    else
        git clone $_gitroot $_gitname
    fi

    msg "GIT checkout done or server timeout."
    msg "Starting make..."
    rm -rf $srcdir/$_gitname-build
    # }}}
}

package(){
    cd $srcdir/$_gitname
    
    install -dm755 ${pkgdir}/usr/bin
    install -Dm755 set_dark.sh          ${pkgdir}/usr/bin/
    install -Dm755 set_light.sh         ${pkgdir}/usr/bin/
    
    install -dm644 ${pkgdir}/usr/share/guake/solarized-colors/"{colors, doc}"
    install -Dm644 colors/*             ${pkgdir}/usr/share/guake/solarized-colors/colors/
    install -Dm644 README.mdk           ${pkgdir}/usr/share/guake/solarized-colors/doc
    
    install -dm644 ${pkgdir}/usr/share/licenses/guake-solarized-colors/
    install -Dm644 LICENSE.mdk          ${pkgdir}/usr/share/licenses/guake-colors-solarized/
}

