# Firefly Jam

A small browser game where playing the game writes the music.

You're a firefly in a night meadow. Catch the glowing notes. Each one plays a chime that fits the current chord and lands exactly on the beat. As your score climbs, instruments join the song one at a time:

| Score | Instrument |
|---|---|
| 0 | Pad |
| 10 | Kick drum |
| 25 | Hi-hats |
| 45 | Bass |
| 70 | Arpeggio |

Dodge the pink static blobs. Hitting one costs a life and resets your combo multiplier. You have three lives.

## How to play

Open `index.html` in any web browser. There's nothing to install.

- **Move:** mouse, finger, or arrow keys / WASD
- **Mute:** the Sound button or the `M` key

## How it works

Everything is in one file, `index.html`:

- **Graphics** are drawn on an HTML `<canvas>`.
- **Music** is generated live with the Web Audio API, using no audio files. A scheduler looks slightly ahead on the audio clock and queues each sixteenth note, and caught notes are snapped to the next sixteenth so they always land in time.
- The song loops through the chords **Am – F – C – G** at 96 BPM.
