# Cloning

This repository contains symbolic links, and also includes other repositories as
submodules. Therefore, special care needs to be taken to properly clone this
repository onto a local system. In particular, Git must be configured to
preserve symbolic links, and submodules must be cloned recursively.

## Configuring Git

The following command configures Git to preserve symbolic links. On Windows, it
may also be necessary to enable [Developer mode][win-dev-mode] to allow the
creation of symbolic links.

```
git config --global core.symlinks true
```

## Cloning recursively

Once Git is configured as above, the following command properly clones this
repository along with all its submodules. Note that the `--recurse-submodules`
option is passed to clone submodules recursively.

```
git clone --recurse-submodules \
  https://github.com/Kenneth-Goveas/CARL-Air-Brake-Peripheral-Devices-Hardware.git
```

[win-dev-mode]: https://learn.microsoft.com/en-us/windows/apps/get-started/enable-your-device-for-development
