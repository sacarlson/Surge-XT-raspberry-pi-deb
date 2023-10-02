# Surge-XT-raspberry-pi-deb
binnary deb install files to install Surge XT synth on a raspberry pi compute

This should install and run on both the Raspberry Pi 3 or Pi 4 but must have the 64 bit arm64 version of the OS istalled.
I only tested the stand alone synth on the Pi 4 with 4gb ram so good luck with Pi 3 if you try that.
to verify your system has 64 bit system running in a command line type getconf LONG_BIT it should return 64  NOT 32.
install deb as you would any other deb file with sudo apt install ./<deb package>

Seems the files are too big for github so I put the files on my google drive hope that's ok:
https://drive.google.com/file/d/19GlzSFBOFh0F4OjKMMcn45gzuWQKQAXZ/view?usp=sharing
https://drive.google.com/file/d/1GJ9MQ0vVE4hJ0ohLsT_6JTb2GZEa75Ee/view?usp=sharing
[https://drive.google.com/drive/folders/1-z40uk8pv3vAiLS1_vHuY_x0Fg1JtzeN?usp=drive_link](https://drive.google.com/drive/folders/1-z40uk8pv3vAiLS1_vHuY_x0Fg1JtzeN?usp=sharing)

to run it just type 'Surge XT' in a term.  I presently am running it in Audio device type: ALSA with bcm2835 Headphones: Direct hardware.
I have not yet tested it with jackd but it looks to have support for that too.
I am using a LinnStrument midi over usb with MPE enaable to drive it directly no added software and let me say it is fantasitc.
I have sample rate set to 48000 Hz and audio buffer set to 256 samples (5.3ms lag)
I just needed a portable synth to play realtime on the road that I could carry so don't have any recorders and stuf setup with it yet.

To compile your own version of surge xt on a Rasbperry pi or other platforms see https://github.com/surge-synthesizer/surge
it took me a lot of trial and error to get it to compile and I couldn't find any other binnary installs for the stand alone synth so I did it myself.
but I must say I never want to do it again.
it took over 1 hour to compile the system and many trail and errors to find what would work that took me about 2 days.
This is what I can remember of what I ended up doing to get it to compile from within a pi 4 computer term.

sudo apt install build-essential libcairo-dev libxkbcommon-x11-dev libxkbcommon-dev libxcb-cursor-dev libxcb-keysyms1-dev libxcb-util-dev libxrandr-dev libxinerama-dev libxcursor-dev libasound2-dev libjack-jackd2-dev cmake
git clone https://github.com/surge-synthesizer/surge.git
cd surge
git submodule update --init --recursive
cmake -Bbuild
cmake --build build --config Release 

To package it to a deb file I used dpkg-deb --build suge-xt-pi-arm64_1.3.main.0d099b37
I analized an uncompressed Surge XT nighly build deb file for ubuntu as an example of what was included in the package and where they put the files.
as you can see by the name of the package I cloned the 1.3.main.0d099b37 version of Surge XT to build this.

I created 2 deb files so far one is a lite version with none of the 4000+ patches that are included in the non lite version.
lite version: suge-xt-lt-pi-arm64_1.3.main.0d099b37.deb  34996kb
none lite version: suge-xt-pi-arm64_1.3.main.0d099b37.deb  181524kb
