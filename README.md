# 🤖 OctoPi-UpToDate

*The latest OctoPi release with the latest OctoPrint already included*

This repository automatically updates the OctoPrint installation, kernel and bootloader on the latest OctoPi image
and provides the resulting image ready to flash. Checkout the [releases](https://github.com/OctoPrint/OctoPi-UpToDate/releases).

## How does this work?

A bunch of simple update scripts are run via [CustoPiZer](https://github.com/OctoPrint/CustoPiZer):

  * `01-update-octoprint`: Updates OctoPrint to the latest version
  * `02-update-boot`: Updates bootloader and kernel to the latest version
  * `10-install-arducam-mjpg-streamer`: Replaces the existing mjpg-streamer with the Arducam fork available [here](https://github.com/ArduCAM/mjpg-streamer).
  * `80-install-user-fix`: Installs a compatibility layer to support renaming the `pi` user, if needed.
  * `81-fix-octopi-txt`: Replaces `/boot/octopi.txt` with one with updated documentation regarding camera options.
  * `99-write-build`: Writes the build tag to `/etc/octopiuptodate-build`

## How do I run this?

There's a [Taskfile](https://taskfile.dev) in this repository that you can use to run the update scripts locally.

  - Install [Taskfile](https://taskfile.dev/installation/)
  - Install [Docker]()
  - Create a `workspace` directory and place your `input.img` in that
  - Run `task build`

Alternatively, you can also manually run `docker`:

```
docker run --rm --privileged -v $(pwd)/workspace:/CustoPiZer/workspace $(pwd)/scripts:/CustoPiZer/workspace/scripts ghcr.io/octoprint/custopizer:latest
```

## Can I do something like this as well?

Sure, check out [CustoPiZer's README](https://github.com/OctoPrint/CustoPiZer) for 
instructions on how to set up your own image build for modified but clean OctoPi images!

## Are these images available on the download page and in the Raspberry Pi Imager?

Yes, they are!

## I have a problem, where's the issue tracker for this project?

Nowhere, because this really is just a build automation.

If you need support with OctoPrint or OctoPi, [please get in touch on the OctoPrint Community Forums](https://community.octoprint.org).
