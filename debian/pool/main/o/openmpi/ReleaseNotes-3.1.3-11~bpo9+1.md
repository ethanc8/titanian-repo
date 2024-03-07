# OpenMPI 3.1.3 for Ubuntu 18.04

The package was built on a Jetson Nano running Ubuntu 18.04, L4T r32.7.4.

```bash
mkdir -p ~/Projects/OpenMPI && cd ~/Projects/OpenMPI
### Build dh-fortran-mod
apt source dh-fortran-mod/buster
cd dh-fortran-mod-*
sudo mk-build-deps --install # Allow it to remove `openmpi-build-deps`
# Add a changelog entry saying that we backported it
dch --bpo
# Allow building with Jetson's malformed shared library metadata
printf "override_dh_shlibdeps:\n\tdh_shlibdeps --dpkg-shlibdeps-params=--ignore-missing-info" >> debian/rules
dpkg-buildpackage --build=binary --unsigned-changes
cd ..
sudo apt install ./dh-fortran-mod*.deb

### Build pmix
apt source pmix/buster
cd pmix-*
sudo mk-build-deps --install # Allow it to remove `openmpi-build-deps`
# Add a changelog entry saying that we backported it
dch --bpo
cd .
# Allow building with Jetson's malformed shared library metadata
printf "override_dh_shlibdeps:\n\tdh_shlibdeps --dpkg-shlibdeps-params=--ignore-missing-info" >> debian/rules
dpkg-buildpackage --build=binary --unsigned-changes
cd ..
sudo apt install ./*pmix*.deb

### Build openmpi
apt source openmpi/buster
cd openmpi-*
sudo mk-build-deps --install # Allow it to remove `openmpi-build-deps`
# Add a changelog entry saying that we backported it
dch --bpo
# Allow building with Jetson's malformed shared library metadata
printf "override_dh_shlibdeps:\n\tdh_shlibdeps --dpkg-shlibdeps-params=--ignore-missing-info" >> debian/rules
dpkg-buildpackage --build=binary --unsigned-changes
cd ..
sudo apt install ./*.deb
```