# kefctl - a command line application for controlling KEF speakers

  This application only requires Perl 5.10.1 or newer to be installed and has no
  other dependencies. So it should run pretty much everywhere without too much
  trouble, especially on Linux.

  To my knowledge there is no documentation about the KEF control protocol. So
  every feature in kefctl had to be reverse engineered by capturing network
  traffic generated by the KEF Control mobile application talking to **KEF LSX**
  and **KEF LS50 Wireless** speakers (Firmware version 4.1).
  
  Turning the KEF LS50 Wireless on only works with the newer revision (new
  electronics), serial number after LS50W13074K24L/R2G or Nocturne Edition.

## Features

  * Turn speakers on and off
  * Change input source
  * Change volume
  * Mute and unmute speakers
  * Standby modes
  * Inverse L/R speakers
  * Check current speaker status

```
Usage: kefctl [OPTIONS]

    kefctl --status
    kefctl --volume 70
    kefctl --raise 5
    kefctl --lower 5
    kefctl --off
    kefctl -i optical
    kefctl -i bluetooth -S 20 -I
    kefctl -H 192.168.178.52 -p 50001 -i aux
    kefctl -r 5330819b0b

  Options:
    -h, --help                  Show this summary of available options
    -H, --host <host>           Speaker host, defaults to 192.168.178.66
    -i, --input <source>        Set input source to aux, bluetooth, optical,
                                usb or wifi
    -I, --inverse               Inverse L/R speakers, this option can only be
                                used together with the --input option
    -L, --lower <percentage>    Lower volume by X percent
    -m, --mute                  Mute speakers
    -o, --off                   Turn speakers off, the KEF LSX can be turned
                                back on by setting an input source with the
                                --input option
    -p, --port <port>           Speaker port, defaults to 50001
    -r, --request <hex>         Send raw request in hex format and show response
                                (very useful for testing speaker features)
    -R, --raise <percentage>    Raise volume by X percent
    -s, --status                Show current speaker status
    -S, --standby <minutes>     Set standby time to 20, 60 or 0 (to turn standby
                                off), this option can only be used together with
                                the --input option
    -u, --unmute                Unmute speakers
    -v, --volume <percentage>   Set volume to a percentage value of 0-100, be
                                aware that every input source has its own volume
                                setting
        --version               Show version

  You can also set the KEFCTL_DEBUG environment variable to get diagnostics
  information printed to STDERR.
  ```

## Copyright and License

  Copyright (C) 2019-2020, Sebastian Riedel.

  This program is free software, you can redistribute it and/or modify it under
  the terms of the Artistic License version 2.0
