virtio-snd
==========

This document explains the setup and usage of the virtio-snd device.
The virtio-snd device is a paravirtualized sound card device.

Linux kernel support
--------------------

virtio-snd requires a guest Linux kernel built with the
``CONFIG_SND_VIRTIO`` option.

Description
-----------

virtio-snd implements capture and playback from inside a guest using the
configured audio backend of the host machine.

Examples
--------

Add a PCI device:

::

  -device virtio-sound-pci,disable-legacy=on

And an audio backend listed with ``-audio driver=help`` that works on
your host machine, e.g.:

 * pulseaudio: ``-audio driver=pa,model=virtio-sound``
   or ``-audio driver=pa,model=virtio-sound,server=/run/user/1000/pulse/native``
 * sdl: ``-audio driver=sdl,model=virtio-sound``
 * coreaudio: ``-audio driver=coreaudio,model=virtio-sound``

etc.
