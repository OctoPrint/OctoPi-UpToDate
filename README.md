# 🤖 OctoPi-UpToDate

*The latest OctoPi release with the latest OctoPrint already included*

This repository automatically updates the OctoPrint installation, kernel and bootloader on the latest OctoPi image
and provides the resulting image ready to flash. Checkout the [releases](https://github.com/OctoPrint/OctoPi-UpToDate/releases).

## How does this work?

A bunch of simple update scripts are run via [CustoPiZer](https://github.com/OctoPrint/CustoPiZer):

  * `01-update-octoprint`: Updates OctoPrint to the latest version
  * `02-update-boot`: Updates bootloader and kernel to the latest version
  * `80-install-user-fix`: Installs a compatibility layer to support renaming the `pi` user, if needed.
  * `99-write-build`: Writes the build tag to `/etc/octopiuptodate-build`

## Can I do something like this as well?

Sure, check out [CustoPiZer's README](https://github.com/OctoPrint/CustoPiZer) for 
instructions on how to set up your own image build for modified but clean OctoPi images!

## Are these images available on the download page and in the Raspberry Pi Imager?

Yes, they are!

## I have a problem, where's the issue tracker for this project?

Nowhere, because this really is just a build automation.

If you need support with OctoPrint or OctoPi, [please get in touch on the OctoPrint Community Forums](https://community.octoprint.org).
