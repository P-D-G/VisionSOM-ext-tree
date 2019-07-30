# VisionSOM-ext-tree
An external buildroot tree for Somlabs VisionSOM-6ULL modules, based on the manufacturer's configuration (see [here](https://github.com/somlabs/somlabs-buildroot)).

This project simply reuses the same config files as an external tree for use with a more recent buildroot version.

# How to use

```bash
git clone https://github.com/P-D-G/VisionSOM-ext-tree.git 
git clone git clone git://git.buildroot.net/buildroot
cd buildroot
make BR2_EXTERNAL=/path/to/VisionSOM-ext-tree/ list-defconfigs
```

The list-defonfigs should show the modules defconfigs ("somlabs_visionsom_6ull..."). The external source tree is persistent and only needs to be specified once. The next operations can be the same as any buildroot project.

```bash
make menuconfig
make
```

For more information on external buildroot customizations, please refer to [buildroot documentation](https://buildroot.org/downloads/manual/manual.html#outside-br-custom).

# Known issue

The *host-mtd* package did not compile properly on my Ubuntu 18.04 machine. The problem can be worked around by adding "host-zstd" on the "HOST_MTD_DEPENDENCIES" of the "package/mtd/mtd.mk" file.
