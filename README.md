

Experiments with media recording, playback and tools
Recommended tools : ffmpeg, bento4

Why we want finer grained control over loading of assets?
Video is order of magnitude larger in file size than audio.
Waste of bandwidth if user downloads entire file and watches
only a part.

HTTP adaptive streaming protocols: HLS, HDS, SSTR, DASH.

PreRequisite: Server should convert high def/high bitrate file file (mezzania source file) etc. and encode/transcode it to 
to multiple renditions(different qualities) 
all broken into multiple chunks + manifest
via some tool like ffmpeg.

   HOw to do your own adaptive bitrate streaming:
1. Parse the manifest (for segment sources/sizes), 
2. Check your bandwidth,
3. fetch(via HTTP) appropriate segment and put it into some
sort of In mem-sourcebuffer etc. where the video/audio 
is playing from.
4. Loop 1, steps 2-4 keep repeating for regular periods

BrowserS:

A browser will make byte range requests on behalf on 
behalf of media element to buffer content.

MSE Apis are codec agnostic

A MediaSource will have one or more SourceBuffer,
Where each SourceBuffer can have one or more ArrayBuffers.

By default html5 video tag DOES NOT do any kind of adaptive streaming,
In order to have adaptive streaming for a plain html5 video tag,
We need some external library like dash.js or https://github.com/videojs/videojs-contrib-hls in addition to video tag to get adaptive streaming.

For a great overall html5 powerful video player
checkout open source project
https://github.com/videojs/video.js


