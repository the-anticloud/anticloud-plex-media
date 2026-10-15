# PLEX_MEDIA

> Anticloud offline package — upstream: plexinc/plex-media-player @ `master`.

## What This Project Does

Next generation Plex Desktop/Embedded Client

## Upstream README

## Deprecation

Note: Plex is no longer actively maintaining Plex Media Player.  This repository is preserved as it was when last developed.  See https://www.plex.tv/media-server-downloads/#plex-app for replacement applications.

## Building

You need:

* Qt 5.9.5
* cmake 3.1 or newer
* ninja is recommended for building
* FFmpeg 3.x and mpv from github

## Building on Mac OS X

Configure

If you're happy just building from the command line then run CMake for the ninja build tool:

* Install ninja with homebrew:
  * ``brew install ninja``
* Install mpv and other dependencies with homebrew:
  * ``brew install mpv --with-shared --HEAD``
* ``mkdir build ; cd build``
* ``cmake -GNinja -DCMAKE_BUILD_TYPE=Debug -DCMAKE_INSTALL_PREFIX=output ..``

Build (ninja):

* ``ninja``

Make a distributable package:

* ``ninja install`` (be patient, it's slow)

Or if you prefer working in Xcode, run CMake for the xcode build):

* ``mkdir build ; cd build``
* ``cmake -GXcode ..``

## Building on Linux

Plex Media Player officially requires Qt 5.9.5. Our users have indicated that Qt 5.10 and Qt 5.11 also builds correctly. However, Qt 5.11.0 and 5.11.1 versions are _incompatible_ and should be avoided. Qt 5.12 may work for you. Please consider building PMP within a dedicated VM or Docker container if your system has a Qt version installed newer than 5.9.5. Downgrading a system Qt will cause issues in other applications depending on a newer Qt version.

These instructions are for Ubuntu 16.04 LTS and up. They were tested on a fresh install without extra options and with auto-updates applied.

First, some preparations:

* ``sudo apt install autoconf automake libtool libharfbuzz-dev libfreetype6-dev libfontconfig1-dev
    libx11-dev libxrandr-dev libvdpau-dev libva-dev mesa-common-dev libegl1-mesa-dev
    yasm libasound2-dev libpulse-dev libuchardet-dev zlib1g-dev libfribidi-dev git
    libgnutls28-dev libgl1-mesa-dev libsdl2-dev cmake``
* ``mkdir pmp``
* ``cd pmp``

Systems not based on Debian/Ubuntu will have similar packages, but you'll need to figure out their names yourself.

### Downloading and installing Qt

If your distro provides a Qt 5.9.5 package, try to use it. Otherwise, download a supported Qt version from qt.io.

On Windows and OSX, you can omit the ``-DQTROOT`` argument to use the Qt built by Plex. (Untested whether this works reliably.)

### Building mpv and ffmpeg

While most distros have FFmpeg and mpv packages, they're often outdated. It's recommended to build a current version, or to get them from 3rd party sources (some are listed on https://mpv.io/installation/).

Here are instructions how to build them locally. First you need to install some build prerequisites:

* ``git clone https://github.com/mpv-player/mpv-build.git``
* ``cd mpv-build``
* ``echo --enable-libmpv-shared > mpv_options``
* you can also add ``echo --disable-cplayer >> mpv_options`` to prevent mpv CLI from being built
* ``./rebuild -j4`` (this steps checks out all sources and compil

## License

Upstream terms preserved in `THIRD_PARTY_LICENSES/`. Overlay licensed under Anticommons 0.1.0.

## Verification

Recompute the SHA3-256 of `BENCH.json` and compare to this package’s register. Any drift = invalid package.
