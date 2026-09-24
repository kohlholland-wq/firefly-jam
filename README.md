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

## Two acts, eight movements

Keep scoring and the song travels through sections, each with its own key, tempo, drum groove and scenery. Changes wait for the end of a musical phrase, with a drum fill and a rising sweep leading in. Each new movement gives you back a life.

### Act I · The Meadow

| Score | Movement | Chords | Tempo | Scenery |
|---|---|---|---|---|
| 0 | I · Moonrise | Am F C G | 96 BPM | Crescent moon |
| 80 | II · Aurora | Em C G D | 104 BPM | Northern lights |
| 170 | III · Rainfall | F♯m D A E | 112 BPM | Rain and lightning |
| 280 | IV · Daybreak | Cmaj7 Am7 Fmaj7 G | 120 BPM | Sunrise |

### Act II · Lantern Town

After Daybreak the firefly reaches a festival town with a brand-new song and a new band. The song starts over with just the pad, and the other instruments join one by one again:

- a **plucked koto-style string**, synthesized with the Karplus-Strong algorithm, for the chimes and arpeggio
- **taiko drum**, **shaker** and **wood block** for the rhythm section
- a **breathy flute** for solos

The static turns icy blue here, and it weaves side to side as it moves.

| Score | Movement | Chords | Tempo | Scenery |
|---|---|---|---|---|
| 420 | V · Dusk Market | D Bm G A | 92 BPM | Rooftops and strings of lanterns |
| 560 | VI · Lantern Rise | Bm G D A | 100 BPM | Sky lanterns float upward |
| 720 | VII · Fireworks | G D Em C | 116 BPM | Fireworks burst on the beat |
| 900 | VIII · Last Light | Gmaj7 F♯m7 Em7 A7 | 104 BPM | A full moon |

## Pickups

- **Notes:** points, plus a chime. Catch them in a row to build a multiplier of up to ×4.
- **Golden star (Solo):** for four bars you play the lead instrument. Your height on the screen sets the pitch, and faint rows labelled with note names show which note each height plays. The rest of the band plays softer so the solo stands out. Nearby notes drift toward you, and points are doubled.
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
