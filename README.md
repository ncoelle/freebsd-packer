FreeBSD Packer Template
=======================

This repository provides a Packer template for building FreeBSD image with ZFS root. The repository is based on [brd/packer-freebsd](https://github.com/brd/packer-freebsd) but use [mfsBSD](http://mfsbsd.vx.sk/) to bootstrap the installation over SSH instead of using boot command with FreeBSD ISO.

## Usage

The resulting image is currently published at [pxfs/freebsd-11.0](https://vagrantcloud.com/pxfs/boxes/freebsd-11.0). You can init Vagrant environment with the image built from this repository with:

```shell
$ vagrant init pxfs/freebsd-11.0
```

Or configure manually,

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "pxfs/freebsd-11.0"
  # Other configuration.
end
```

## Manually Building

* [Vagrant](https://www.vagrantup.com/)
* [Packer](https://www.packer.io/)
* [VirtualBox](https://www.virtualbox.org/) (for VirtualBox image)
* [VMware Provider](https://www.vagrantup.com/vmware) (for VMware image)

### Building

1. Build the Vagrant box with `packer build template.json`.
2. Add the Vagrant box with `vagrant box add --name freebsd-11.0 freebsd-11.0-vmware.box`.

The default Vagrantfile comes with NFS mount on `/vagrant` and 1GB of RAM with 20GB of disk.
