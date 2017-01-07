MPVCTL
======

mpvctl is a simple program that intends to help manage mpv playback globally by
taking adventage of its ipc feature, and letting you preserve settings through
configuration.

Currently only volume control is implemented (but it saves it and allows you to listen your music in background while watching your youtube video without sound fights, while enjoying your favourite ALSA), more things will come soon (in a low priority).
Feel free to build upon, you can mention me tho ;).

Configuration
-------------

You can use command options if you want (I wouldn't do that, it looks messy, but
theyre there). I suggest rather creating a configuration (`.mpvctlrc`) file in your `~`.

Example bellow (notice lack of spaces and comments, theyre important):
```cfg
mpv-config=$HOME/.config/mpv/mpv.conf
mpv-section=ytv
mpv-ipc=/tmp/mpvsocket
```

That way everything is declared explicitly, of course rather than specyfying mpv-ipc,
you can decrease redundancy by letting mpvctl get it from mpv config section.

So aside from that you need mpv to create ipc socket for you. Do that by
specyfying `input-ipc-server` in the section you provided.

Let me show you! (`mpv.conf`)
```
... defaults (no we don't use them

[ytv]
input-ipc-server=/tmp/mpvsocket
... your options

... more of your sections sections
```

Now everythings almost fine. If you start mpv with --profile=ytv, mpvctl should
work. So make sure to add this option to your mpv invocation.

Usage
-----

#### Options
...
Let's skip the options.

#### Commands

* volume [+|-]value
    right now the only command supported. If +/- are present then the command
    will increase/decrease volume. Otherwise the volume will be set to given
    value

#### Example

```bash
mpvctl volume +5
```

Aint that awesome? :D
