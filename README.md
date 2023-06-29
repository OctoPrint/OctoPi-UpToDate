# 🤖 OctoPi-UpToDate

*The latest OctoPi release with the latest OctoPrint already included*

This repository automatically updates the OctoPrint installation, kernel and bootloader on the latest OctoPi image
and provides the resulting image ready to flash. Checkout the [releases](https://github.com/OctoPrint/OctoPi-UpToDate/releases).

## How does this work?

A bunch of simple update scripts are run via [CustoPiZer](https://github.com/OctoPrint/CustoPiZer):

  * `00-enforce-32bit-kernel`: Ensures only 32bit kernels are installed (since RPi kernel 6.1 64bit will be installed even on 32bit)
  * `01-add-octoprint-apt-repo`: Adds `apt.octoprint.org` to the apt sources
  * `02-update-octoprint`: Updates OctoPrint to the latest version
  * `03-update-boot`: Updates bootloader and kernel to the latest version
  * `04-update-libcamera-apps`: Updates the the libcamera apps to the latest version
  * `10-install-camera-streamer`: Installs the new [camera-streamer](https://github.com/ayufan/camera-streamer) based webcam stack, replacing mjpg-streamer and webcamd. The new stack supports libcamera based cameras like the RPi Cam v3 and newer Arducams, and is also more performant. See [the FAQ](https://faq.octoprint.org/camera-streamer-config) for more details.
  * `11-install-pb`: Installs a small script under `/usr/local/bin/pb` that allows to easily share stdin or a text file to paste.octoprint.org.
  * `80-install-user-fix`: Installs a compatibility layer to support renaming the `pi` user, if needed.
  * `99-write-build`: Writes the build tag to `/etc/octopiuptodate-build`

## How do I run this?

There's a [Taskfile](https://taskfile.dev) in this repository that you can use to run the update scripts locally.

  - Install [Taskfile](https://taskfile.dev/installation/)
  - Install [Docker](https://www.docker.com/)
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

If you need support with OctoPrint or OctoPi, [please get in touch on the OctoPrint Community Forums](https://community.octoprint.org).

For issues *specific to this project*, please [open an issue here](https://github.com/OctoPrint/OctoPi-UpToDate/issues/new?template=bug_report.yml). Please note that the only issues accepted here are those related to *modifications* done by this build process, as described above.

Anything not touched by the modification scripts should *not* be reported here, but rather on the [OctoPi issue tracker](https://github.com/guysoft/OctoPi/issues).
