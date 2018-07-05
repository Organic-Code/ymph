# ymph

Youtube Music Playlist Helper (ymph) is a script designed to help you to play youtube playlist in the background, together with a daemonized music player (such as MPD)

It currently only supports vlc but can be easily adapted by editing the first few lines, in which case you won't need 'vlc-ctl' and 'vlcd' (this will be configurable in the future)

## Dependencies

ymph has the following dependencies (arch linux package names):

* bash
* coreutils 
* ffmpeg
* grep
* jq
* procps-ng
* sed
* util-linux
* youtube-dl

to check for those dependencies, you may run 'ymph --deps-chk'.

If you choose to use vlcd and vlc-ctl, following depencies are added:

* openbsd-netcat
* vlc

## Usage

Available options:

	--help                   -h  print this text and exit

	--url <playlist_url>     -u  URL to the youtube playlist
	--save-as <save_file>    -s  save the playlist to the given file
	                             The file can be used with --file later on
	                             To be used with --url
	--file <playlist_file>   -f  use the specified playlist, previously saved with --save-as.
	                             Cannot be used together with --save-as
	                             If --url is not specified, it will take a default value.
	                             defaults to $XDG_MUSIC_DIR/ymph.playlist,
	                                      or $HOME/Music/ymph.playlist if $XDG_MUSIC_DIR is not set
	--random                 -r  randomize the music order
	--normalize              -N  normalize audio file after download (disabled by default)
	                             [! might take some time]
	--no-cache                   delete audio files after playing them
	--next                 next  skip current music
	                             An instance of ymph should already be running and have the same temp directory
	--prev                 prev  Back to previous music
	                             An instance of ymph should already be running and have the same temp directory
	                             This command is supported only if the playlist was not randomized
	--stop                 stop  stop the player
	                             An instance of ymph should already be running and have the same temp directory
	--pause               pause  pause the player
	                             An instance of ymph should already be running and have the same temp directory
	--play                 play  resume the player
	                             An instance of ymph should already be running and have the same temp directory
	--play-pause     play-pause  toggle play/pause
	                             An instance of ymph should already be running and have the same temp directory

	--load-ahead <N>             Specify the number of audio files to load ahead. Defaults to 3.
	--show-cache                 Show the list of files in cache folder. Any subsequent argument is ignored
	--search <regex>             Search a particular music in the cache. Any subsequent argument is ignored
	--clear-cache                Clears the cache. Any subsequent argument is ignored
	--deps-chk                   Check dependencies. Any subsequent argument is ignored
	--download-dir <folder>  -d  specifies a folder where to download audio file
	                             Defaults to $XDG_CACHE_HOME/ymph,
	                                      or $HOME/.cache/ymph if $XDG_CACHE_HOME is not set
	--temp-dir <folder>          specifies a folder where to put temporary files.
	                             Defaults to $XDG_RUNTIME_DIR, or /tmp/$UID if $XDG_RUNTIME_DIR is not set

