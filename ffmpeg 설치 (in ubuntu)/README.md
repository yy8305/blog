# 개요 (Overview)
- ubuntu 환경에서 ffmpeg 설치 방법 입니다.

# 설치법
```
$ sudo apt-get update -qq && sudo apt-get -y install \
    autoconf \
    automake \
    build-essential \
    cmake \
    git-core \
    libass-dev \
    libfreetype6-dev \
    libgnutls28-dev \
    libsdl2-dev \
    libtool \
    libva-dev \
    libvdpau-dev \
    libvorbis-dev \
    libxcb1-dev \
    libxcb-shm0-dev \
    libxcb-xfixes0-dev \
    pkg-config \
    texinfo \
    wget \
    yasm \
    zlib1g-dev

$ mkdir -p ~/ffmpeg_sources ~/bin

$ sudo apt-get install nasm

$ sudo apt-get install libx264-dev

$ sudo apt-get install libx265-dev libnuma-dev

$ sudo apt-get install libvpx-dev

$ sudo apt-get install libfdk-aac-dev

$ sudo apt-get install libmp3lame-dev

$ sudo apt-get install libopus-dev

$ cd ~/ffmpeg_sources && \
wget -O ffmpeg-snapshot.tar.bz2 https://ffmpeg.org/releases/ffmpeg-snapshot.tar.bz2 && \
tar xjvf ffmpeg-snapshot.tar.bz2 && \
cd ffmpeg && \
PATH="$HOME/bin:$PATH" PKG_CONFIG_PATH="$HOME/ffmpeg_build/lib/pkgconfig" ./configure \
  --prefix="$HOME/ffmpeg_build" \
  --pkg-config-flags="--static" \
  --extra-cflags="-I$HOME/ffmpeg_build/include" \
  --extra-ldflags="-L$HOME/ffmpeg_build/lib" \
  --extra-libs="-lpthread -lm" \
  --bindir="$HOME/bin" \
  --enable-gpl \
  --enable-libass \
  --enable-libfdk-aac \
  --enable-libfreetype \
  --enable-libmp3lame \
  --enable-libopus \
  --enable-libvorbis \
  --enable-libvpx \
  --enable-libx264 \
  --enable-libx265 \
  --enable-nonfree && \
PATH="$HOME/bin:$PATH" make && \
make install && \
hash -r

$ echo "MANPATH_MAP $HOME/bin $HOME/ffmpeg_build/share/man" >> ~/.manpath


# ~/bin 에 있는거 /usr/local/bin 으로 복사
$ cp ~/bin/* /usr/local/bin/
```

# 참고 url
- https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu

- https://linuxconfig.org/ubuntu-20-04-ffmpeg-installation   (in ubuntu 20.04)