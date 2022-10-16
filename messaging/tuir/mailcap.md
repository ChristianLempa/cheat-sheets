# Tuir example mailcap

```
# Example mailcap file for Terminal UI for Reddit
# https://gitlab.com/ajak/tuir/
#
# Copy the contents of this file to {HOME}/.mailcap, or point to it using $MAILCAPS
# Then launch TUIR using the --enable-media flag. All shell commands defined in
# this file depend on external programs that must be installed on your system.
#
# HELP REQUESTED! If you come up with your own commands (especially for OS X)
# and would like to share, please post an issue on the GitHub tracker and we
# can get them added to this file as references.
#
#
#                              Mailcap 101
# - The first entry with a matching MIME type will be executed, * is a wildcard
# - %s will be replaced with the image or video url
# - Add ``test=test -n "$DISPLAY"`` if your command opens a new window
# - Add ``needsterminal`` for commands that use the terminal
# - Add ``copiousoutput`` for commands that dump text to stdout

###############################################################################
# Commands below this point will open media in a separate window without
# pausing execution of TUIR.
###############################################################################

# Feh is a simple and effective image viewer
# Note that tuir returns a list of urls for imgur albums, so we don't put quotes
# around the `%s`
image/x-imgur-album; feh -g 640x480  -. %s; test=test -n "$DISPLAY"
image/pdf; qpdfview %s; test=test -n "$DISPLAY"; nametemplate=%s.pdf
image/x-pdf; qpdfview %s; test=test -n "$DISPLAY"; nametemplate=%s.pdf
image/gif; mpv '%s' --autofit=640x480 --loop=inf; test=test -n "$DISPLAY"
image/gif; xnview %s; test=test -n "$DISPLAY"
image/gif; eom %s; test=test -n "$DISPLAY"
image/bmp; xnview %s; test=test -n "$DISPLAY"
image/jpeg; xnview %s; test=test -n "$DISPLAY"
image/png; xnview %s; test=test -n "$DISPLAY"
image/tiff; xnview %s; test=test -n "$DISPLAY"
image/*; curl -s '%s' | /usr/bin/display-im6.q16 -; test=test -n "$DISPLAY"

video/mpeg; vlc %s; description="MPEG Video"; test=test -n "$DISPLAY"
video/x-mpeg; vlc %s; description="MPEG Video"; test=test -n "$DISPLAY"
video/mpeg-system; vlc %s; description="MPEG Video"; test=test -n "$DISPLAY"
video/x-mpeg-system; vlc %s; description="MPEG Video"; test=test -n "$DISPLAY"
video/mpeg4; vlc %s; description="MPEG-4 Video"; test=test -n "$DISPLAY"
video/3gpp; /usr/bin/mplayer %s; description="3GPP multimedia file"; test=test -n "$DISPLAY"
video/3gpp2; /usr/bin/mplayer %s; description="3GPP2 multimedia file"; test=test -n "$DISPLAY"
video/dv; /usr/bin/mplayer %s; description="DV video"; test=test -n "$DISPLAY"
video/x-flic; /usr/bin/mplayer %s; description="FLIC animation"; test=test -n "$DISPLAY"
video/x-flv; /usr/bin/mplayer %s; description="Flash video"; test=test -n "$DISPLAY"
video/x-matroska; /usr/bin/mplayer %s; description="Matroska video"; test=test -n "$DISPLAY"
video/mp2t; /usr/bin/mplayer %s; description="MPEG-2 transport stream"; test=test -n "$DISPLAY"
video/mp4; /usr/bin/mplayer %s; description="MPEG-4 video"; test=test -n "$DISPLAY"
video/mpeg; /usr/bin/mplayer %s; description="MPEG video"; test=test -n "$DISPLAY"
video/x-ms-asf; /usr/bin/mplayer %s; description="Microsoft ASF video"; test=test -n "$DISPLAY"
video/x-ms-wmv; /usr/bin/mplayer %s; description="Windows Media video"; test=test -n "$DISPLAY"
video/x-msvideo; /usr/bin/mplayer %s; description="AVI video"; test=test -n "$DISPLAY"
video/x-nsv; /usr/bin/mplayer %s; description="NullSoft video"; test=test -n "$DISPLAY"
video/ogg; /usr/bin/mplayer %s; description="Ogg Video"; test=test -n "$DISPLAY"
video/x-ogm+ogg; /usr/bin/mplayer %s; description="OGM video"; test=test -n "$DISPLAY"
video/quicktime; /usr/bin/mplayer %s; description="QuickTime video"; test=test -n "$DISPLAY"
video/vnd.rn-realvideo; /usr/bin/mplayer %s; description="RealVideo document"; test=test -n "$DISPLAY"
video/x-theora+ogg; /usr/bin/mplayer %s; description="Ogg Theora video"; test=test -n "$DISPLAY"
video/webm; /usr/bin/mplayer %s; description="WebM video"; test=test -n "$DISPLAY"
video/x-ms-asf; clementine --next %s; test=test -n "$DISPLAY"
video/webm; firefox -private-window %s; test=test -n "$DISPLAY"
video/mpeg; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-mpeg2; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-mpeg3; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/mp4v-es; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-m4v; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/mp4; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/divx; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/vnd.divx; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/msvideo; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-msvideo; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/ogg; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/quicktime; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/vnd.rn-realvideo; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-ms-afs; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-ms-asf; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-ms-wmv; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-ms-wmx; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-ms-wvxvideo; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-avi; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/avi; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-flic; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/fli; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-flc; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/flv; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-flv; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-theora; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-theora+ogg; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-matroska; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/mkv; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/webm; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-ogm; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/x-ogm+ogg; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/mp2t; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/vnd.mpegurl; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/3gp; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/3gpp; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/3gpp2; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/dv; mpv --player-operation-mode=pseudo-gui -- %s; test=test -n "$DISPLAY"
video/3gp; totem --fullscreen %s; test=test -n "$DISPLAY"
video/3gpp; totem --fullscreen %s; test=test -n "$DISPLAY"
video/3gpp2; totem --fullscreen %s; test=test -n "$DISPLAY"
video/dv; totem --fullscreen %s; test=test -n "$DISPLAY"
video/divx; totem --fullscreen %s; test=test -n "$DISPLAY"
video/fli; totem --fullscreen %s; test=test -n "$DISPLAY"
video/flv; totem --fullscreen %s; test=test -n "$DISPLAY"
video/mp2t; totem --fullscreen %s; test=test -n "$DISPLAY"
video/mp4; totem --fullscreen %s; test=test -n "$DISPLAY"
video/mp4v-es; totem --fullscreen %s; test=test -n "$DISPLAY"
video/mpeg; totem --fullscreen %s; test=test -n "$DISPLAY"
video/mpeg-system; totem --fullscreen %s; test=test -n "$DISPLAY"
video/msvideo; totem --fullscreen %s; test=test -n "$DISPLAY"
video/ogg; totem --fullscreen %s; test=test -n "$DISPLAY"
video/quicktime; totem --fullscreen %s; test=test -n "$DISPLAY"
video/vivo; totem --fullscreen %s; test=test -n "$DISPLAY"
video/vnd.divx; totem --fullscreen %s; test=test -n "$DISPLAY"
video/vnd.mpegurl; totem --fullscreen %s; test=test -n "$DISPLAY"
video/vnd.rn-realvideo; totem --fullscreen %s; test=test -n "$DISPLAY"
video/vnd.vivo; totem --fullscreen %s; test=test -n "$DISPLAY"
video/webm; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-anim; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-avi; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-flc; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-fli; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-flic; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-flv; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-m4v; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-matroska; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-mjpeg; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-mpeg; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-mpeg2; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-ms-asf; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-ms-asf-plugin; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-ms-asx; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-msvideo; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-ms-wm; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-ms-wmv; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-ms-wmx; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-ms-wvx; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-nsv; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-ogm+ogg; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-theora; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-theora+ogg; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-totem-stream; totem --fullscreen %s; test=test -n "$DISPLAY"
video/x-ms-asf; picard %s; test=test -n "$DISPLAY"
video/x-theora; picard %s; test=test -n "$DISPLAY"
video/x-wmv; picard %s; test=test -n "$DISPLAY"
video/ogg; shotcut %s; test=test -n "$DISPLAY"
video/x-ogm+ogg; shotcut %s; test=test -n "$DISPLAY"
video/x-theora+ogg; shotcut %s; test=test -n "$DISPLAY"
video/x-theora; shotcut %s; test=test -n "$DISPLAY"
video/x-ms-asf; shotcut %s; test=test -n "$DISPLAY"
video/x-ms-asf-plugin; shotcut %s; test=test -n "$DISPLAY"
video/x-ms-asx; shotcut %s; test=test -n "$DISPLAY"
video/x-ms-wm; shotcut %s; test=test -n "$DISPLAY"
video/x-ms-wmv; shotcut %s; test=test -n "$DISPLAY"
video/x-ms-wmx; shotcut %s; test=test -n "$DISPLAY"
video/x-ms-wvx; shotcut %s; test=test -n "$DISPLAY"
video/x-msvideo; shotcut %s; test=test -n "$DISPLAY"
video/divx; shotcut %s; test=test -n "$DISPLAY"
video/msvideo; shotcut %s; test=test -n "$DISPLAY"
video/vnd.divx; shotcut %s; test=test -n "$DISPLAY"
video/x-avi; shotcut %s; test=test -n "$DISPLAY"
video/vnd.rn-realvideo; shotcut %s; test=test -n "$DISPLAY"
video/mp2t; shotcut %s; test=test -n "$DISPLAY"
video/mpeg; shotcut %s; test=test -n "$DISPLAY"
video/mpeg-system; shotcut %s; test=test -n "$DISPLAY"
video/x-mpeg; shotcut %s; test=test -n "$DISPLAY"
video/x-mpeg2; shotcut %s; test=test -n "$DISPLAY"
video/x-mpeg-system; shotcut %s; test=test -n "$DISPLAY"
video/mp4; shotcut %s; test=test -n "$DISPLAY"
video/mp4v-es; shotcut %s; test=test -n "$DISPLAY"
video/x-m4v; shotcut %s; test=test -n "$DISPLAY"
video/quicktime; shotcut %s; test=test -n "$DISPLAY"
video/x-matroska; shotcut %s; test=test -n "$DISPLAY"
video/webm; shotcut %s; test=test -n "$DISPLAY"
video/3gp; shotcut %s; test=test -n "$DISPLAY"
video/3gpp; shotcut %s; test=test -n "$DISPLAY"
video/3gpp2; shotcut %s; test=test -n "$DISPLAY"
video/vnd.mpegurl; shotcut %s; test=test -n "$DISPLAY"
video/dv; shotcut %s; test=test -n "$DISPLAY"
video/x-anim; shotcut %s; test=test -n "$DISPLAY"
video/x-nsv; shotcut %s; test=test -n "$DISPLAY"
video/fli; shotcut %s; test=test -n "$DISPLAY"
video/flv; shotcut %s; test=test -n "$DISPLAY"
video/x-flc; shotcut %s; test=test -n "$DISPLAY"
video/x-fli; shotcut %s; test=test -n "$DISPLAY"
video/x-flv; shotcut %s; test=test -n "$DISPLAY"
video/mpeg; vlc -I rc -V caca %s; needsterminal; description="MPEG Video"
video/x-mpeg; vlc -I rc -V caca %s; needsterminal; description="MPEG Video"
video/mpeg-system; vlc -I rc -V caca %s; needsterminal; description="MPEG Video"
video/x-mpeg-system; vlc -I rc -V caca %s; needsterminal; description="MPEG Video"
video/mpeg4; vlc -I rc -V caca %s; needsterminal; description="MPEG-4 Video"
video/x-msvideo; vlc %s; description="MS Video (AVI)"; test=test -n "$DISPLAY"
video/quicktime; vlc %s; description="Apple Quicktime Video"; test=test -n "$DISPLAY"
video/ogg; vlc %s; description="Ogg Video"; test=test -n "$DISPLAY"
video/x-msvideo; vlc -I rc -V caca %s; needsterminal; description="MS Video (AVI)"
video/quicktime; vlc -I rc -V caca %s; needsterminal; description="Apple Quicktime Video"
video/ogg; vlc -I rc -V caca %s; needsterminal; description="Ogg Video"
video/ogg; ogginfo '%s'; copiousoutput

# Youtube videos are assigned a custom mime-type, which can be streamed with
# vlc or youtube-dl.
video/x-youtube; vlc '%s' --width 640 --height 480; test=test -n "$DISPLAY"
video/x-youtube; mpv --ytdl-format=bestvideo+bestaudio/best '%s' --autofit=640x480; test=test -n "$DISPLAY"

# Use vlc
video/*; vlc %s > /dev/null; test=test -n "$DISPLAY"
# Mpv is a simple and effective video streamer
video/*; mpv '%s' --autofit=640x480 --loop=inf; test=test -n "$DISPLAY"

###############################################################################
# Commands below this point will attempt to display media directly in the
# terminal when a desktop is not available (e.g. inside of an SSH session)
###############################################################################

# View images directly in your terminal with iTerm2
# curl -L https://iterm2.com/misc/install_shell_integration_and_utilities.sh | bash
# image/*; bash -c '[[ "%s" == http*  ]] && (curl -s %s | ~/.iterm2/imgcat) || ~/.iterm2/imgcat %s' && read -n 1; needsterminal

# View true images in the terminal, supported by rxvt-unicode, xterm and st
# Requires the w3m-img package
# image/*; w3m -o 'ext_image_viewer=off' '%s'; needsterminal

# Don't have a solution for albums yet
image/x-imgur-album; echo

# 256 color images using half-width unicode characters
# Much higher quality than img2txt, but must be built from source
# https://github.com/rossy/img2xterm
# image/*; curl -s '%s' | convert -resize 80x80 - jpg:/tmp/tuir.jpg && img2xterm /tmp/tuir.jpg; needsterminal; copiousoutput

# Display images in 256 colors using jp2a in Asciiville
image/*; curl -s '%s' | convert -resize 80x80 - jpg:/tmp/tuir.jpg && jp2a --border --colors --term-fit /tmp/tuir.jpg; copiousoutput

# Full motion videos - requires a framebuffer to view
video/x-youtube; mpv -vo drm -quiet '%s'; needsterminal
video/*; mpv -vo drm -quiet '%s'; needsterminal

# Ascii videos
# video/x-youtube; youtube-dl -q -o - '%s' | mplayer -cache 8192 -vo caca -quiet -; needsterminal
# video/*; wget '%s' -O - | mplayer -cache 8192 -vo caca -quiet -; needsterminal
```
