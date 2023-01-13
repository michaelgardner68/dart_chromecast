### Find the IP address of your chromecast on mac OS

This is the way I found the IP address of my ChromeCast on my Mac. This is not guaranteed to work for everyone, 
but if it helps anyone, here are the terminal commands:

`$ dns-sd -B _googlecast local`

Copy the instance name

`$ dns-sd -L <IntanceName> _googlecast._tcp. local.`

Copy the name (without the port) directly after the text '<IntanceName> can be reached at '...

`$ dns-sd -Gv4v6 <Paste>`

---

## usage

### options
**media** space separated list of one or more media source urls

**host** (optional) IP address of a ChromeCast device in the same network that you are on.

**port** (optional) port of the ChromeCast device. Defaults to `8009`.

### flags
**--append** (-a) whether to append the passed in media to the current playlist and not replace the current playlist (if reconnecting was successful). Defaults to `false`.  
**--debug** (-d) whether to show all info logs, defaults to `false`.

### usage
`dart example/index.dart <media> [--host <host> [--port <port> [--append [ --debug]]]]` 

### playback control
In this demo the following keys can be used to control the playback of the video:

`space` toggle paused state \
`s` stop playback \
`esc` disconnect device \
`left arrow key` seek -10 seconds \
`right arrow key` seek +10 seconds

### example
`dart index.dart http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/ForBiggerFun.mp4`

### reconnecting to active session
When you exit the command line without disconnecting the device, the video will keep playing. 
To reconnect without messing with the current playlist, just run the command without any media urls. Eg:

`dart index.dart --host=192.168.1.1`
