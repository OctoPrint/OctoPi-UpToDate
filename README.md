# 🤖 OctoPi-UpToDate

*The latest OctoPi release with the latest OctoPrint already included*

This repository automatically updates the OctoPrint installation on the latest OctoPi image
and provides the resulting image ready to flash. Checkout the [releases](https://github.com/OctoPrint/OctoPi-UpToDate/releases).

## How does this work?

A simple update script is run via [CustoPiZer](https://github.com/OctoPrint/CustoPiZer).
All that is done is running the equivalend of `pip install -U OctoPrint==<latest version>`.

## Can I do something like this as well?

Sure, check out [CustoPiZer's README](https://github.com/OctoPrint/CustoPiZer) for 
instructions on how to set up your own image build for modified but clean OctoPi images!

## Will these images become available on the download page and in the Raspberry Pi Imager?

That's the plan, but that first requires this automation to get some more testing. It's been wired up into OctoPrint's 
release workflow now, so next OctoPrint release should show if it that triggers a build correctly. If that works,
some further automation needs to be written to automatically update the web page with a link to the latest image
and also generate a release file for the imager.
