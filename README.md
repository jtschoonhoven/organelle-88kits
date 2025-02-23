# organelle-88kits
Sampled drum kits for Organelle in Pure Data.

https://drive.google.com/file/d/1Ee5OVXG7CAtv7mv6Va8c97rrWvllh0l0/view

Drum kits are created by adding a folder that contains at least one WAV file that matches the name of a drum from the MIDI spec. E.g. a simple kit might consist of three WAV files, "Acoustic Bass Drum.wav", "Acoustic Snare.wav" and "Closed Hi-hat.wav", in a folder named "Vintage Acoustic".

| Midi | Name               | Type I              | Type II    |
|------|--------------------|---------------------|------------|
|  35  | Acoustic Bass Drum | Drums               | Bass       |
|  36  | Bass Drum 1        | Drums               | Bass       |
|  86  | Mute Surdo         | Drums               | Bass       |
|  87  | Open Surdo         | Drums               | Bass       |
|  41  | Low Floor Tom      | Drums               | Low Tom    |
|  43  | High Floor Tom     | Drums               | Low Tom    |
|  45  | Low Tom            | Drums               | Low Tom    |
|  47  | Low-Mid Tom        | Drums               | Mid Tom    |
|  48  | High Mid Tom       | Drums               | Mid Tom    |
|  61  | Low Bongo          | Drums               | Mid Tom    |
|  64  | Low Conga          | Drums               | Mid Tom    |
|  66  | Low Timbale        | Drums               | Mid Tom    |
|  50  | High Tom           | Drums               | High Tom   |
|  60  | High Bongo         | Drums               | High Tom   |
|  62  | Mute High Conga    | Drums               | High Tom   |
|  63  | Open High Conga    | Drums               | High Tom   |
|  65  | High Timbale       | Drums               | High Tom   |
|  37  | Side Stick         | Snares & Claps      | Snare      |
|  38  | Acoustic Snare     | Snares & Claps      | Snare      |
|  40  | Electric Snare     | Snares & Claps      | Snare      |
|  28  | Slap               | Snares & Claps      | Clap       |
|  39  | Hand Clap          | Snares & Claps      | Clap       |
|  88  | Applause           | Snares & Claps      | Clap       |
|  31  | Sticks             | Blocks & Bells      | Hit        |
|  85  | Castanets          | Blocks & Bells      | Hit        |
|  75  | Claves             | Blocks & Bells      | Hit        |
|  76  | High Wood Block    | Blocks & Bells      | Hit        |
|  77  | Low Wood Block     | Blocks & Bells      | Hit        |
|  78  | Mute Cuica         | Blocks & Bells      | Hit        |
|  79  | Open Cuica         | Blocks & Bells      | Hit        |
|  56  | Cowbell            | Blocks & Bells      | Bell       |
|  53  | Ride Bell          | Blocks & Bells      | Bell       |
|  67  | High Agogo         | Blocks & Bells      | Bell       |
|  68  | Low Agogo          | Blocks & Bells      | Bell       |
|  27  | High Q             | Blocks & Bells      | Click      |
|  32  | Square Click       | Blocks & Bells      | Click      |
|  33  | Metronome Click    | Blocks & Bells      | Click      |
|  34  | Metronome Bell     | Blocks & Bells      | Click      |
|  42  | Closed Hi-hat      | Cymbals             | Hat        |
|  44  | Pedal Hi-hat       | Cymbals             | Hat        |
|  46  | Open Hi-hat        | Cymbals             | Hat        |
|  49  | Crash Cymbal 1     | Cymbals             | Crash      |
|  51  | Ride Cymbal 1      | Cymbals             | Crash      |
|  52  | Chinese Cymbal     | Cymbals             | Crash      |
|  55  | Splash Cymbal      | Cymbals             | Crash      |
|  57  | Crash Cymbal 2     | Cymbals             | Crash      |
|  59  | Ride Cymbal 2      | Cymbals             | Crash      |
|  54  | Tambourine         | Shakers & Scratches | Shaker     |
|  70  | Maracas            | Shakers & Scratches | Shaker     |
|  82  | Shaker             | Shakers & Scratches | Shaker     |
|  29  | Scratch Push       | Shakers & Scratches | Scratch    |
|  30  | Scratch Pull       | Shakers & Scratches | Scratch    |
|  58  | Vibra-slap         | Shakers & Scratches | Scratch    |
|  69  | Cabasa             | Shakers & Scratches | Scratch    |
|  71  | Short Whistle      | Shakers & Scratches | Scratch    |
|  72  | Long Whistle       | Shakers & Scratches | Scratch    |
|  73  | Short Guiro        | Shakers & Scratches | Scratch    |
|  74  | Long Guiro         | Shakers & Scratches | Scratch    |
|  80  | Mute Triangle      | Shakers & Scratches | Jingles    |
|  81  | Open Triangle      | Shakers & Scratches | Jingles    |
|  83  | Jingle Bell        | Shakers & Scratches | Jingles    |
|  84  | Bell Tree          | Shakers & Scratches | Jingles    |

    _________________________________________________________
    |  | | | |  |  | | | | | |  |  | | | |  |  | | | | | |  |
    |  | | | |  |  | | | | | |  |  | | | |  |  | | | | | |  |
    |  | | | |  |  | | | | | |  |  | | | |  |  | | | | | |  |
    |  |_| |_|  |  |_| |_| |_|  |  |_| |_|  |  |_| |_| |_|  |
    |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
    | C | D | E | F | G | A | B | C | D | E | F | G | A | B |
    |___|___|___|___|___|___|___|___|___|___|___|___|___|___|

    |-C---D---E-|                  |-Db-Eb------Gb-Ab-Bb-|
 Basses, Toms & Tonal            Cymbals, Shakers & Scratches

                |-F---G---A---B-|
          Snares, Claps, Blocks & Bells

On Load:
1. Get the list of all drum samples in the kit folder
2. Split that list into 3 new lists, one for each cluster above
3. Count the number of samples in each list
4. Load all samples into memory

On Note Press:
1. Identify which cluster the pressed note belongs to
2. Get the cluster index of that note where E3=-1, C4=0, D4=1, E4=2, C5=3, etc.
3. Match the index to a sample in the corresponding list (using modulus arithmetic as needed)
4. If the index is in the list (quotient=0) then play the corresponding sample as-is; or
5. If the index is not in the list (quotient!=0) then play the corresponding sample pitched up or down a fifth
