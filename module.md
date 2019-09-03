# Module

TRDG is also a module that can be included in your favorite training pipeline. The easiest way to use it, is to import a generator.

```py
from TextRecognitionDataGenerator.generators import GeneratorFromStrings

generator = GeneratorFromStrings(['Test1', 'Test2', 'Test3'])

for img in generator:
    # Do something with the pillow image here.
```

The basic one is `GeneratorFromStrings` which, as its name indicates, will take a list of strings, and generate an image and label pair.

If you want to avoid having to maintain dictionaries, you can use `GeneratorFromDicts` which will use the bundled ones, `GeneratorFromRandom` which generates random strings, and `GeneratorFromWikipedia` which picks random article from Wikipedia as its source for strings.

Here are examples for each of those, respectively:

```py
from TextRecognitionDataGenerator.generators import (
    GeneratorFromDicts,
    GeneratorFromRandom,
    GeneratorFromWikipedia,
)

generator_from_dicts = GeneratorFromDicts()
generator_from_random = GeneratorFromRandom()
generator_from_wikipedia = GeneratorFromWikipedia()

for img, lbl in generator_from_dicts:
    # Do something with the pillow image here.
```

**The generators will not raise StopIteration, they will keep generating images until you break out of the loop. Set a non-negative value for `count` if that's an issue**