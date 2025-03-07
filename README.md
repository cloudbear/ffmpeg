# Minimal FFmpeg Docker image built on Alpine Linux

Current FFmpeg version: `5.1.2`

## FFmpeg Build Configuration

```sh
ffmpeg version 5.1.2 Copyright (c) 2000-2022 the FFmpeg developers
  built with gcc 12.2.1 (Alpine 12.2.1_git20220924-r4) 20220924
  configuration: 
    --enable-version3
    --enable-gpl
    --enable-nonfree
    --enable-small
    --enable-libmp3lame
    --enable-libx264
    --enable-libx265
    --enable-libvpx
    --enable-libtheora
    --enable-libvorbis
    --enable-libopus
    --enable-libass
    --enable-libwebp
    --enable-librtmp
    --enable-postproc
    --enable-libfreetype
    --enable-openssl
    --disable-debug
  libavutil      57. 28.100 / 57. 28.100
  libavcodec     59. 37.100 / 59. 37.100
  libavformat    59. 27.100 / 59. 27.100
  libavdevice    59.  7.100 / 59.  7.100
  libavfilter     8. 44.100 /  8. 44.100
  libswscale      6.  7.100 /  6.  7.100
  libswresample   4.  7.100 /  4.  7.100
  libpostproc    56.  6.100 / 56.  6.100
```

## Usage

```sh
docker run opencoconut/ffmpeg -i http://files.coconut.co.s3.amazonaws.com/test.mp4 -f webm -c:v libvpx -c:a libvorbis - > test.webm
```

To encode a local file, you can mount the current path on the Docker host's filesystem as a volume inside the container like this:

```sh
docker run -v=`pwd`:/tmp/ffmpeg opencoconut/ffmpeg -i localfile.mp4 out.webm
```

You can create an alias so you use the Docker container like if FFmpeg is installed on your computer:

In `~/.bashrc`:

```sh
alias ffmpeg='docker run -v=`pwd`:/tmp/ffmpeg opencoconut/ffmpeg'
```

Now we can execute FFmpeg with just:

```sh
ffmpeg -buildconf
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## Original Author

**Bruno Celeste** [http://coconut.co](http://coconut.co)

[@OpenCoconut](http://twitter.com/OpenCoconut)

You can contact me directly on Twitter [@brunoceleste](http://twitter.com/brunoceleste)
