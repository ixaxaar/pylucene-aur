# Maintainer: Russi <ixaxaar@mailbox.org> <aur@ixaxaar.in>

pkgname=pylucene
pkgver=9.10.0
pkgrel=1
pkgdesc="Python bindings for Apache Lucene"
arch=('x86_64')
url="https://lucene.apache.org/pylucene/"
license=('Apache')
depends=('jdk-openjdk' 'gradle' 'python' 'gcc' 'make' 'ant' 'python-setuptools')
makedepends=('git')
source=(
    "https://downloads.apache.org/lucene/pylucene/pylucene-$pkgver-src.tar.gz"
)
sha256sums=('SKIP') # RRuntime Environmeplace with the actual checksum

prepare() {
    # Set environment variables for JCC build
    JAVA_BIN=$(which java)
    JAVA_HOME=$(dirname $(dirname $(readlink -f $JAVA_BIN)))
    export JCC_JDK=$JAVA_HOME
    export JCC_INCLUDES="$JAVA_HOME/include:$JAVA_HOME/include/linux"
    export JCC_LFLAGS="-L$JAVA_HOME/lib/server -ljvm"

    PYTHON_BIN=$(which python3)
    PREFIX_PYTHON=$(dirname $(dirname $(readlink -f $PYTHON_BIN)))
    export PYTHON=${PREFIX_PYTHON}/bin/python3
    export JCC="${PYTHON} -m jcc --shared"
    export NUM_FILES=16
}

build() {
    cd "$srcdir/pylucene-$pkgver/jcc"

    python setup.py build
    python setup.py install --user

    cd "$srcdir/pylucene-$pkgver"

    make || true
}

check() {
    cd "$srcdir/pylucene-$pkgver"
    make test
}

package() {
    JAVA_BIN=$(which java)
    JAVA_HOME=$(dirname $(dirname $(readlink -f $JAVA_BIN)))
    export JCC_JDK=$JAVA_HOME
    export JCC_INCLUDES="$JAVA_HOME/include:$JAVA_HOME/include/linux"
    export JCC_LFLAGS="-L$JAVA_HOME/lib/server -ljvm"

    cd "$srcdir/pylucene-$pkgver"
    make install
}
