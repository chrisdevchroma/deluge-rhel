# deluge-rhel
Forked from https://src.fedoraproject.org/rpms/deluge.git to build for RHEL/CentOS 8

## How to build
1. Install the Development tools (includes rpm-build)
```bash
sudo dnf group install "Development Tools"
```
2. Install rpmdevtools (for spectool)
```bash
sudo dnf install rpmdevtools
```
3. Install deluge build dependencies
```bash
sudo dnf install python3-devel python3-wheel
```
4. Build deluge dependency rb_libtorrent-python3 -> see https://github.com/chrisdevchroma/rb_libtorrent-rhel
5. Clone repo with git and cd into the folder
6. Create build/SOURCES dir
```bash
mkdir -p build/SOURCES
```
7. Download deluge source tarball with spectool
```bash
spectool -g -C build/SOURCES deluge.spec
```
8. Build package with rpmbuild
```bash
 rpmbuild --define "_topdir `pwd`/build" -ba deluge.spec
 ```
