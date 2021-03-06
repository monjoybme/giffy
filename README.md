giffy
=====

command line tool for creating animated gifs from videos

![futurama](https://github.com/jpwright/giffy/blob/master/farnsworth.gif?raw=true)

Requirements
------------
The following packages: `avconv`, `gifsicle`, and `imagemagick`. Use `apt-get` or `yum` to install.

I have only tested on Ubuntu 12.04 LTS.

Installation
------------
`git clone https://github.com/jpwright/giffy.git`

Command line options
--------------------

    OPTIONS:
       -h, --help             Show this message
       -i, --input            Input file. Can be a wide variety of formats, try 'avconv -formats' to see a list.
       -o, --output           Output file. 
       -s, --start            Start timestamp. Can be a number of seconds or in hh:mmss[.xxx] form.
       -d, --duration         Duration. Should be a number of seconds (decimals OK)
       -r, --resize           Resize operator. Can be a percentage (50%) or a width in pixels (50). Default is 100%.
       -t, --caption          Caption operator. Should be a string, for example '-caption 'caption words here''. You can insert linebreaks into the caption by inserting '\n'.
       -l, --caption-height   Line height of caption, either as a percentage or in number of pixels.
       -f, --fps              Frames per second for the output gif. Default is 24. Max is 48.
       -z, --optimize         Optimization level. Default (and maximum) is 3.
       -c, --compress         Enable compression to 256 colors. Will reduce output filesize at the expense of quality.
       -v, --verbose          Verbose output.
   
Examples
--------

### Bare minimum
To make a gif called `out.gif` from a movie `in.mp4` consisting of the first 3 seconds:<br />
`giffy -i in.mp4 -o out.gif -s 0 -d 3`

### Resizing
To make that gif half the size in each dimension:<br />
`giffy -i in.mp4 -o out.gif -s 0 -d 3 -r 50%`

To force that gif to be 200 pixels wide:<br />
`giffy -i in.mp4 -o out.gif -s 0 -d 3 -r 200`

### Captioning
To add a caption:<br />
`giffy -i in.mp4 -o out.gif -s 0 -d 3 -t "Hello world"`

To add a caption with multiple lines:<br />
`giffy -i in.mp4 -o out.gif -s 0 -d 3 -t "Hello world\nGoodbye world"`

To add a caption with line height 24px:<br />
`giffy -i in.mp4 -o out.gif -s 0 -d 3 -t "Hello world" -l 24`

To add a caption with line height 10% of the output gif:<br />
`giffy -i in.mp4 -o out.gif -s 0 -d 3 -t "Hello world" -l 10%`

### Speedup
To animate at 36 fps:<br />
`giffy -i in.mp4 -o out.gif -s 0 -d 3 -f 36`

Note that the default is 24, regardless of the fps of the input movie.

### Optimization
To change the gif optimization level:<br />
`giffy -i in.mp4 -o out.gif -s 0 -d 3 -z 1`

See the [gifsicle manpage](http://www.lcdf.org/gifsicle/man.html) for an explanation of gif optimization levels.<br />

To compress to 256 colors:<br />
`giffy -i in.mp4 -o out.gif -s 0 -d 3 -c`


