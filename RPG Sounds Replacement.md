With RPG Sounds more-or-less abandonware and already having some stability issues, it may be a good idea to build a FOSS replacement.

Requirements
- Ability to play as many formats as possible, including WAV, MP3, M4A, OGG, WMA, and any other formats in my music library.
- Ability to transmit audio over VBAN.  This would enable not having to run a separate applet to do so.  Needs to include IPv6 support.
- In-place audio library.  Importing should not be required beyond pointing to library root directories.
- Full Unicode support.  RPG Sounds has issues with non-English characters in audio metadata.
- Display of audio metadata, including title, album, author, album art, and more.
- Multi-source staging and mixing.  Like RPG Sounds, the user should be able to drag audio from their library view to a staging/mixing grid where multiple sources can be played concurrently.
- Playlist staging.  Multiple audio files should be able to be staged in the same slot to be played in sequence or shuffled, perhaps even with the ability to cross-fade.
- Responsive streaming from disk.  The application should not have to pre-load entire audio files before being able to play them, but it also should be able to start a staged source without the user having to wait.  If waiting is necessary, there at least needs to be an indication that the load is in progress.
- Stage saving.  The user's stage should be retained between sessions, and multiple stages would be great.
- Soundboard.  In addition to the stage for longer audio tracks, there should be a separate stage for short clips to be played on-demand.  Due to their short length and the need for responsiveness, soundboard clips would need to be fully loaded at all times.
- Preview audio source.  It would be nice for the user to be able to preview sounds through a separate configurable audio device so that previews can be done privately.
- Light and dark modes.  I hate light mode and Luyou hates dark mode.
- Drag-and-drop from library to stage.

Tech
- Likely C++ with Qt