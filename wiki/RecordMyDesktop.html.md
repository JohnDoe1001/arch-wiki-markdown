RecordMyDesktop
===============

recordMyDesktop is screencasting software for X. It can record audio
through ALSA, OSS or the JACK audio server. It is the only screencasting
software able capture through jack and thus is important for pro-audio
video tutorials. recordMyDesktop only outputs to Ogg using Theora for
video and Vorbis for audio.

recordMyDesktop is a CLI tool but there are two GUI interfaces
available, gtk-recordmydesktop and qt-recordmydesktop.

Contents
--------

-   1 Installation
-   2 Usage
-   3 Troubleshooting
    -   3.1 Audio record is lagging
    -   3.2 Audio record lags and is out of sync
    -   3.3 Audio record is distorted (slower/graver)
    -   3.4 No sound with PulseAudio
-   4 External Links

Installation
------------

The packages recordmydesktop, gtk-recordmydesktop and qt-recordmydesktop
can be found in [community].

Usage
-----

The basic usage is not too hard and it provides a man page. Here is a
simple example using jack for audio capture:

    $ recordmydesktop --use-jack system:capture_1

Troubleshooting
---------------

Current versions behave weird and need strange parameters to work
properly. Try this for non-choppy capture:

    $ recordmydesktop --use-jack system:capture_1 --v_bitrate 2000000

> Audio record is lagging

If it appears that you have lags (error message when starting from the
shell: Broken pipe: Overrun occurred) in your audio record (often with
Intel onboard cards) then it might help to change the audio device. This
can be done in two ways.

1. Assuming that the terminal version is used then recordmydesktop
should be started with:

    $ recordmydesktop --device plughw:0,0

2. If a GUI is used then you can change the device from DEFAULT to
plghw:0,0 in the audio tab of the settings.

More information on this issue can be found here.

> Audio record lags and is out of sync

Using the plughw:0,0 device as described above may work partially for
some Intel cards. You might try:

    $ recordmydesktop --device plughw:0,0 --freq 22050 --channels 2

It seems the trick was to specify the correct number of channels
generated by the input source (in this case, a stereo mic).

> Audio record is distorted (slower/graver)

This happens at least with Rode Podcaster USB Microphone, and can be
fixed by setting the frequency to 45000:

    $ recordmydesktop --device plughw:2,0 --freq 45000 --channels 2

> No sound with PulseAudio

This is pretty simple, but should be better explained. If
recordmydesktop exits like this:

    Couldn't open PCM device hw:0,0
    Error while opening/configuring soundcard hw:0,0
    Try running with the --no-sound or specify a correct device.

Just run it like:

    $ recordmydesktop --device pulse

External Links
--------------

-   recordMyDesktop Homepage

Retrieved from
"https://wiki.archlinux.org/index.php?title=RecordMyDesktop&oldid=249231"

Categories:

-   X Server
-   Audio/Video

-   This page was last modified on 4 March 2013, at 15:14.
-   Content is available under GNU Free Documentation License 1.3 or
    later unless otherwise noted.
-   Privacy policy
-   About ArchWiki
-   Disclaimers