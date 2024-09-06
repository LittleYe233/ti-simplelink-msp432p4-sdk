pkgname=ti-simplelink-msp432p4-sdk
pkgver=3.40.01.02
pkgrel=2
pkgdesc=""
arch=('x86_64')
license=('custom')

# lib32-glibc needed for the installer
makedepends=('lib32-glibc' 'lib32-fakeroot')

_name=simplelink_msp432p4_sdk_${pkgver//./_}
_installer=${_name}.run

# To download the file, you need to manually navigate to the website, create an
# account, and accept the license for this software. Otherwise, this pkgbuild
# would download an HTML page that will fail the checksum check. Once you accepted
# the license, then you can either download the file manually and place it in
# the folder with this PKGBUILD, or you could paste the identifier that appears
# in the final download URL from TI website into this variable:
_gda=

source=("local://${_installer}")

md5sums=("SKIP") # TI website lists the MD5 sum specifically

options=(!strip libtool staticlibs emptydirs !purge !zipman)

_installdir=opt/ti

prepare() {
    cd $srcdir
    chmod +x ./${_installer}
}

package() {
    echo ">>> Running installer..."
    ./${_installer} --mode unattended --prefix $pkgdir/${_installdir}

    install -D -m0644 $pkgdir/${_installdir}/${_name}/license_${_name}.txt $pkgdir/usr/share/licenses/$pkgname/LICENSE
}
