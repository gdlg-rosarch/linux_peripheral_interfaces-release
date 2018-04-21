# Script generated with Bloom
pkgdesc="ROS - A ROS node for using libsensors to provide diagnostics information about the sensors on a computer system."
url='http://ros.org/wiki/libsensors_monitor'

pkgname='ros-kinetic-libsensors-monitor'
pkgver='0.2.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('lm_sensors'
'ros-kinetic-catkin'
'ros-kinetic-diagnostic-updater'
'ros-kinetic-roscpp'
)

depends=('lm_sensors'
'ros-kinetic-diagnostic-updater'
'ros-kinetic-roscpp'
)

conflicts=()
replaces=()

_dir=libsensors_monitor
source=()
md5sums=()

prepare() {
    cp -R $startdir/libsensors_monitor $srcdir/libsensors_monitor
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

