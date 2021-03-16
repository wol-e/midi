# spc_tools
a bash scripts wrapping some popular spc tools from windows

Basically some scripts to conveniently handle common spc tasks for Super Mario World (SMW) Music creation via SPC's like
- Creating an spc from a txt file via Addmusick
- Playback of spc via SPC Player 700
- Converting spc to wav (development version)

## Requirements

You need to have
- wine installed (tested version wine-3.0 (Ubuntu 3.0-1ubuntu1))
- Downloaded Addmusick (aka AMK, tested version is 1.0.6)
- Downloaded SNES SPC700 Player

## Setup

After downloading this directory the script 'spc_tool' needs to be marked as an executable via running `chmod +x scp_tool` on command line working inside the directory where the file 'spc_tool' is located (aka the directory of this readme). After this you cann call the script from command line via running `spc_tool` or maybe `./spc_tool` from this directory (if you know a little bit more you can move it somewhere else and add it to your path to call it from any folder)

An important setup step is you **need to set the directory variables where AMK and SPC Player are located inside the spc_tool file**. For that simply open the file 'spc_tool' in an editor and set the variables `spc700_dir` and `amk_dir` to the paths to where they are located on your machine (i.e. they need to point at the (extracted) folder which you downloaded to get those tools). For example my setup is:

`spc700_dir="/home/wolle/Music/rom_music/SPC700 PLAYER"`

`amk_dir='/home/wolle/Music/rom_music/AMK/AddmusicK_1.0.6'`

If you don't want to refer to the scripts location when using it you cann add teh script to your path. For example this can be achieved by adding a symbolic link to your users personal binaries directory at `~/bin` (if it does not exist you can just create the directory):

`ln -s ./spc_tool ~/bin/spc_tool`

## Usage

To display an overview of it's usage on the command line simply run `./spc_tool -h`. Then you will see this output, which should get you everywhere:

-h   display this help text
play   launches SPC 700 Player via wine and plays spc file provided as 2nd argument.
build   converts a composition in .txt format via AddmusicK and wine to an .spc file.
wav   converts an .spc file to a .wav audio file via ffmpeg (in development, results may be poor)

For example,

- if you want to create an .spc file 'test.spc' from an existing composition 'test.txt' you need to run
`./spc_tool build test.txt test.spc`

- if you want to playback an .spc file, say 'test.spc', run `./spc_tool play test.spc`.

- if you want to convert an .spc to .wav run for example `./spc_tool wav test.spc test.wav 00:05:30` (note: since an spc is intended to loop, when ceonverting you need to parse a duration for the target wav file, since the programm would not know how often to loop. This feature is in development and will be improved hopefully).
