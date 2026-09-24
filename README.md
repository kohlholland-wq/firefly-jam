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

## Four movements

Keep scoring and the song travels through four sections, each with its own key, tempo, drum groove and sky. Changes wait for the end of a musical phrase, with a drum fill and a rising sweep leading in. Each new movement gives you back a life.

| Score | Movement | Chords | Tempo | Sky |
|---|---|---|---|---|
| 0 | I · Moonrise | Am F C G | 96 BPM | Crescent moon |
| 80 | II · Aurora | Em C G D | 104 BPM | Northern lights |
| 170 | III · Rainfall | F♯m D A E | 112 BPM | Rain and lightning |
| 280 | IV · Daybreak | Cmaj7 Am7 Fmaj7 G | 120 BPM | Sunrise |

## Pickups

- **Notes:** points, plus a chime. Catch them in a row to build a multiplier of up to ×4.
- **Golden star (Solo):** for four bars you play lead synth. Your height on the screen sets the pitch, so flying up and down plays a melody. Nearby notes drift toward you, and points are doubled.
- **Hush ring:** appears when the static gets crowded. It sends out a shockwave that pops every static blob, one per sixteenth note, and each pop plays a note of a rising arpeggio.
- **Static (avoid):** the pink spiky blobs. Hitting one costs a life and resets your multiplier.

## How to play

Open `index.html` in any web browser. There's nothing to install.

- **Move:** mouse, finger, or arrow keys / WASD
- **Mute:** the Sound button or the `M` key

## How it works

Everything is in one file, `index.html`:

- **Graphics** are drawn on an HTML `<canvas>`.
- **Music** is generated live with the Web Audio API, using no audio files. A scheduler looks slightly ahead on the audio clock and queues each sixteenth note. Anything you trigger, like a caught note or a popped blob, is snapped to the next sixteenth so it always lands in time.
- **Visual cues** such as the kick-drum glow, the chord name and lightning are queued with the same audio timestamps, so what you see stays in step with what you hear.
- Curious? Open your browser's developer console and type `fireflyJam.state` to peek at the game while it runs.
