SaijPi
======

Developing
----------

Requirements
~~~~~~~~~~~~

#. `qemu-arm-static <http://packages.debian.org/sid/qemu-user-static>`_
#. Downloaded `Raspbian <http://www.raspbian.org/>`_ image.
#. root privileges for chroot
#. Bash
#. git
#. realpath
#. sudo (the script itself calls it, running as root without sudo won't work)

Build SaijPi
~~~~~~~~~~~~

SaijPi can be built from Debian, Ubuntu, Raspbian, or even SaijPi.
Build requires about 2.5 GB of free space available.
You can build it by issuing the following commands::

    sudo apt-get install gawk util-linux realpath qemu-user-static git
    
    git clone https://github.com/Saij/SaijPi.git
    cd SaijPi/src/image
    
    wget https://downloads.raspberrypi.org/raspbian_lite_latest -O jessie-lite-raspbian.zip
    - or -
    wget https://downloads.raspberrypi.org/raspbian_latest -O jessie-raspbian.zip

    cd ..
    sudo modprobe loop
    sudo bash -x ./build
    
Building SaijPi Variants
~~~~~~~~~~~~~~~~~~~~~~~~

SaijPi supports building variants, which are builds with changes from the main release build. An example and other variants are available in the folder ``src/variants/example``.

To build a variant use::

    sudo bash -x ./build [Variant]
    
Usage
~~~~~

#. If needed, override existing config settings by creating a new file ``src/config.local``. You can override all settings found in ``src/config``. If you need to override the path to the Raspbian image to use for building SaijPi, override the path to be used in ``ZIP_IMG``. By default the most recent file matching ``*-raspbian.zip`` found in ``src/image`` will be used.
#. Run ``src/build`` as root.
#. The final image will be created at the ``src/workspace``