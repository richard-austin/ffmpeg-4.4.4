# ffmpeg-4.4.4
FFmpeg README
=============

FFmpeg is a collection of libraries and tools to process multimedia content
such as audio, video, subtitles and related metadata.

## Libraries

* `libavcodec` provides implementation of a wider range of codecs.
* `libavformat` implements streaming protocols, container formats and basic I/O access.
* `libavutil` includes hashers, decompressors and miscellaneous utility functions.
* `libavfilter` provides a mean to alter decoded Audio and Video through chain of filters.
* `libavdevice` provides an abstraction to access capture and playback devices.
* `libswresample` implements audio mixing and resampling routines.
* `libswscale` implements color conversion and scaling routines.

## Tools

* [ffmpeg](https://ffmpeg.org/ffmpeg.html) is a command line toolbox to
  manipulate, convert and stream multimedia content.
* [ffplay](https://ffmpeg.org/ffplay.html) is a minimalistic multimedia player.
* [ffprobe](https://ffmpeg.org/ffprobe.html) is a simple analysis tool to inspect
  multimedia content.
* Additional small tools such as `aviocat`, `ismindex` and `qt-faststart`.

## Documentation

The offline documentation is available in the **doc/** directory.

The online documentation is available in the main [website](https://ffmpeg.org)
and in the [wiki](https://trac.ffmpeg.org).

### Examples

Coding examples are available in the **doc/examples** directory.
## License

FFmpeg codebase is mainly LGPL-licensed with optional components licensed under
GPL. Please refer to the LICENSE file for detailed information.

## Contributing

Patches should be submitted to the ffmpeg-devel mailing list using
`git format-patch` or `git send-email`. Github pull requests should be
avoided because they are not part of our review process and will be ignored.

Use With [security-cam](https://github.com/richard-austin/security-cam) NVR
======

Version of ffmpeg from 5 onwards do not re-multiplex well from RTSP from surveillance cameras 
to fragmented MP$ to the media server when there is an audio track. This is
because (my cameras at least) do not have the necessary time stamps and 
ffmpeg continuously complains that "pts has no value". The resulting re multiplexed
fragmented mp4 has very slow from updates and so is unusable. This version 4 build produces a usable fragmented mp4 stream.

### The NVR installer loads the [ffmpeg 4.4.4 executable](https://github.com/richard-austin/ffmpeg-4.4.4/releases/download/1.0.0/ffmpeg) (for arm64) from the release area of this repo.
Building ffmpeg-4.4.4 
==
#### The source code in this repo originates from https://ffmpeg.org/releases/ffmpeg-4.4.4.tar.xz. The code in the tar file needs a patch applied to compile correctly: -
```text
patch -u -b  ./libavcodec/x86/mathops.h mathopts.patch 
```
Then build with
```text
./configure
make
```
#### The source code in this repository has already had the patch applied, so you can just use: -

```text
./configure
make
```

