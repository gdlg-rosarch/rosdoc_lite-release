# Script generated with Bloom
pkgdesc="ROS - This ROS package wraps documentation tools like doxygen, sphinx, and epydoc, making it convenient to generate ROS package documentation. It also generates online documentation for the ROS wiki."
url='http://wiki.ros.org/rosdoc_lite'

pkgname='ros-kinetic-rosdoc-lite'
pkgver='0.2.7_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
)

depends=('doxygen'
'epydoc'
'python2-catkin_pkg'
'python2-kitchen'
'python2-rospkg'
'python2-sphinx'
'python2-yaml'
'ros-kinetic-genmsg'
)

conflicts=()
replaces=()

_dir=rosdoc_lite
source=()
md5sums=()

prepare() {
    cp -R $startdir/rosdoc_lite $srcdir/rosdoc_lite
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

