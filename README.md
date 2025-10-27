# mpv-jellyfin
[mpv](https://github.com/mpv-player/mpv) plugin that turns it into a [Jellyfin](https://jellyfin.org/) client

## Features

- Minimal Jellyfin client that integrates into mpv
- Navigate your libraries and play files
- Some basic metadata is shown for each item
- If an item is unwatched, it's description is hidden to prevent spoilers
- When a video file finishes playing, it will be marked as watched

## Installation

Copy the .lua file in `scripts/` to your mpv scripts directory (See [mpv's manual](https://mpv.io/manual/master/#files)).

## Configuration

Can be configured through the usual `script-opts` mechanism of mpv (see its [manual](https://mpv.io/manual/master/#files)). The file [`jellyfin.conf`](script-opts/jellyfin.conf) in this repository contains a detailed list of options.

## Usage

By default, the Jellyfin menu can be toggled with `ctrl+j`.

You can navigate around using the arrow keys.

When you activate a video in the menu, it will begin to play that file.

## Limitations

In general this is a very minimal script and isn't designed to be a full Jellyfin client. Changing settings or metadata has to be done from a real Jellyfin client.

Thumbnails will accumulate if the selected image path isn't tmpfs. In addition thumbnails are raw bgra, which means they are less space efficient than the source images from the Jellyfin server.

## Fork changes

1. Change how curl is called to avoid url encoding issues
2. Remove features that I don't use. This includes:
  - Loading of images
  - `use_playlist` configuration
3. Add playback start, stop and progress reporting
4. Add Windows support
  - Still needs the curl binary
  - I recommend installing it via scoop or something similar
5. Use `mp.input` instead of external dependency when using search
  - TODO: Fix jank when returning from search output to normal menu
6. Formatted the code using stylua

## Credit

Thank you to the original author for their work at [EmperorPenguin18/mpv-jellyfin](https://github.com/EmperorPenguin18/mpv-jellyfin)
without which this fork would not have existed. This has been my primary method of consuming Jellyfun content for a long time so
I really appreciate their work.
