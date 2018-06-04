# talkr-apng

`talkr-apng` is forked from the excellent [apng-js](https://github.com/davidmz/apng-js) library which provides a generalized APNG parsing framework.  `talkr-apng` adds functionality specific to playing APNG files in sync with audio or text-to-speech animations.  Similar to talkr's [GIF parsing library](https://github.com/talkr-app/gif-talkr), `talkr-apng` has special code to play blink and eyebrow animations on files that were generated from the iOS app [talkr](https://talkrapp).  Memory use and loading times are drastically reduced by `talkr-apng` as compared to `gif-talkr` because the png frames are compressed.
 
## Usage
`npm install talkr-apng`
 
## API

Please refer to ([apng-js](https://github.com/davidmz/apng-js)) documentation on parseAPNG or the APNG, Player and Frame objects.

The play_for_duration function was added to the player, which will ping-pong for duration on regular APNG files and ping-pong on the first 21 frames of talkr APNG files while overlaying some eyebrows and blinks.

## Creating APNG files

### talkr GIFs 

A conversion script (convert.sh) is provided to transform GIF files generated by [talkr](https://talkrapp) into PNG files that can be used with this library.  It relies on [imagemagick](https://www.imagemagick.org/) and [apngasm](http://apngasm.sourceforge.net/).

### normal GIFs

Any conversion library like [gif2apng](http://gif2apng.sourceforge.net/) will let you create compatible PNG files from standard GIF files.  But there is some skill required to choose animations that will look good in sync with text-to-speech. Try to find input files that start with a closed mouth, then open the mouth in the first few frames.  Any movements (especially in the early frames) will be repeated frequently, so try to find input with minimal head movement in the early frames.

### 29-frame bug

Currently, all 29-frame PNG files are considered talkr files. This will be fixed, but for now, all 29-frame PNG files that weren't generated by talkr will display incorrectly.

