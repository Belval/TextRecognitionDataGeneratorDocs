# Overview

## Most useful arguments

1. `-i`, `--input_file`

    Use it when the provided dictionaries do not fit your usecase. Each line
    will become an image, if your `-c` parameter is high enough.

2. `-c`, `--count`

    Self-explanatory parameter, but one you will probably want to change. The
    default value is 1000.

3. `-l`, `--language`

    This argument is especially important if you want to generate data using a
    specific script. It changes the dictionary to be used (`-l fr` is equivalent
    to `-i dicts/fr.txt`), but most importantly it changes the default fonts to
    take one that supports the language's script. Passing a chinese dictionary without
    changing the language will cause invalid images to be generated.

4. `-t`, `--thread_count`

    Another self-explanatory parameter, yet very important as most computers these days
    ship with a multi-core CPU. Setting this to `-t 8` makes TRDG create 8 processes
    to generate the data.

5. `-f`, `--format`

    By default, all generated images will be 32 pixels high (or wide if you use `-or 1`).
    Now that might be too small for you. `-f` allows you to make bigger images.

## Getting help

As with most CLI tools, TRDG's help is accessible through the `-h` argument.

If you need more information on a specific argument, find its definition
in the reference. If even that does not do, feel free to
[open an issue](https://github.com/Belval/TextRecognitionDataGenerator/issues/new)
on the official repository.

```
usage: run.py [-h] [--output_dir [OUTPUT_DIR]] [-i [INPUT_FILE]]
              [-l [LANGUAGE]] [-c [COUNT]] [-rs] [-let] [-num] [-sym]
              [-w [LENGTH]] [-r] [-f [FORMAT]] [-t [THREAD_COUNT]]
              [-e [EXTENSION]] [-k [SKEW_ANGLE]] [-rk] [-wk] [-bl [BLUR]]
              [-rbl] [-b [BACKGROUND]] [-hw] [-na NAME_FORMAT]
              [-d [DISTORSION]] [-do [DISTORSION_ORIENTATION]] [-wd [WIDTH]]
              [-al [ALIGNMENT]] [-or [ORIENTATION]] [-tc [TEXT_COLOR]]
              [-sw [SPACE_WIDTH]]

Generate synthetic text data for text recognition.

optional arguments:
  -h, --help            show this help message and exit
  --output_dir [OUTPUT_DIR]
                        The output directory
  -i [INPUT_FILE], --input_file [INPUT_FILE]
                        When set, this argument uses a specified text file as
                        source for the text
  -l [LANGUAGE], --language [LANGUAGE]
                        The language to use, should be fr (French), en
                        (English), es (Spanish), de (German), or cn (Chinese).
  -c [COUNT], --count [COUNT]
                        The number of images to be created.
  -rs, --random_sequences
                        Use random sequences as the source text for the
                        generation. Set '-let','-num','-sym' to use
                        letters/numbers/symbols. If none specified, using all
                        three.
  -let, --include_letters
                        Define if random sequences should contain letters.
                        Only works with -rs
  -num, --include_numbers
                        Define if random sequences should contain numbers.
                        Only works with -rs
  -sym, --include_symbols
                        Define if random sequences should contain symbols.
                        Only works with -rs
  -w [LENGTH], --length [LENGTH]
                        Define how many words should be included in each
                        generated sample. If the text source is Wikipedia,
                        this is the MINIMUM length
  -r, --random          Define if the produced string will have variable word
                        count (with --length being the maximum)
  -f [FORMAT], --format [FORMAT]
                        Define the height of the produced images if
                        horizontal, else the width
  -t [THREAD_COUNT], --thread_count [THREAD_COUNT]
                        Define the number of thread to use for image
                        generation
  -e [EXTENSION], --extension [EXTENSION]
                        Define the extension to save the image with
  -k [SKEW_ANGLE], --skew_angle [SKEW_ANGLE]
                        Define skewing angle of the generated text. In
                        positive degrees
  -rk, --random_skew    When set, the skew angle will be randomized between
                        the value set with -k and it's opposite
  -wk, --use_wikipedia  Use Wikipedia as the source text for the generation,
                        using this paremeter ignores -r, -n, -s
  -bl [BLUR], --blur [BLUR]
                        Apply gaussian blur to the resulting sample. Should be
                        an integer defining the blur radius
  -rbl, --random_blur   When set, the blur radius will be randomized between 0
                        and -bl.
  -b [BACKGROUND], --background [BACKGROUND]
                        Define what kind of background to use. 0: Gaussian
                        Noise, 1: Plain white, 2: Quasicrystal, 3: Pictures
  -hw, --handwritten    Define if the data will be "handwritten" by an RNN
  -na NAME_FORMAT, --name_format NAME_FORMAT
                        Define how the produced files will be named. 0:
                        [TEXT]_[ID].[EXT], 1: [ID]_[TEXT].[EXT] 2: [ID].[EXT]
                        + one file labels.txt containing id-to-label mappings
  -d [DISTORSION], --distorsion [DISTORSION]
                        Define a distorsion applied to the resulting image. 0:
                        None (Default), 1: Sine wave, 2: Cosine wave, 3:
                        Random
  -do [DISTORSION_ORIENTATION], --distorsion_orientation [DISTORSION_ORIENTATION]
                        Define the distorsion's orientation. Only used if -d
                        is specified. 0: Vertical (Up and down), 1: Horizontal
                        (Left and Right), 2: Both
  -wd [WIDTH], --width [WIDTH]
                        Define the width of the resulting image. If not set it
                        will be the width of the text + 10. If the width of
                        the generated text is bigger that number will be used
  -al [ALIGNMENT], --alignment [ALIGNMENT]
                        Define the alignment of the text in the image. Only
                        used if the width parameter is set. 0: left, 1:
                        center, 2: right
  -or [ORIENTATION], --orientation [ORIENTATION]
                        Define the orientation of the text. 0: Horizontal, 1:
                        Vertical
  -tc [TEXT_COLOR], --text_color [TEXT_COLOR]
                        Define the text's color, should be either a single hex
                        color or a range in the ?,? format.
  -sw [SPACE_WIDTH], --space_width [SPACE_WIDTH]
                        Define the width of the spaces between words. 2.0
                        means twice the normal space width
```
