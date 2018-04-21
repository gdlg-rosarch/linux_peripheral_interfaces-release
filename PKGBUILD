# Script generated with Bloom
pkgdesc="ROS - Simple script to check battery status"
url='http://ros.org/wiki/laptop_battery_monitor'

pkgname='ros-kinetic-laptop-battery-monitor'
pkgver='0.2.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-diagnostic-msgs'
'ros-kinetic-sensor-msgs'
)

depends=('ros-kinetic-diagnostic-msgs'
'ros-kinetic-rospy'
'ros-kinetic-sensor-msgs'
)

conflicts=()
replaces=()

_dir=laptop_battery_monitor
source=()
md5sums=()

prepare() {
    cp -R $startdir/laptop_battery_monitor $srcdir/laptop_battery_monitor
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

