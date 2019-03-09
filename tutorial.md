# Tutorial

TextRecognitionDataGenerator comes with an (hopefully) easy to use CLI. The tutorial
is actually multiple tutorials, combined in a single page. Feel free to skip sections
that are not relevant to your use case.

## Just generating data

Fun fact, you don't need to use any command line arguments if you want English data
generated using multiple fonts. Indeed, simply running `python3 run.py` will create
1000 English, single word images in the `out/` directory such as these:

![](_static/images/tutorial/1/1.jpg "1")
![](_static/images/tutorial/1/2.jpg "2")
![](_static/images/tutorial/1/3.jpg "3")
![](_static/images/tutorial/1/4.jpg "4")
![](_static/images/tutorial/1/5.jpg "5")
![](_static/images/tutorial/1/6.jpg "6")
![](_static/images/tutorial/1/7.jpg "7")
![](_static/images/tutorial/1/8.jpg "8")
![](_static/images/tutorial/1/9.jpg "9")
![](_static/images/tutorial/1/10.jpg "10")
![](_static/images/tutorial/1/11.jpg "11")
![](_static/images/tutorial/1/12.jpg "12")

Now maybe 1000 is too many or too few for your usecase. You can add the `-c` argument
to set how many examples will be generated.

`python3 run.py -c 10`

As expected, you will find 10 examples in the `out/` directory.

## Generating Chinese data

This is a common usecase, and one that is easy with TRDG.

`python3 run.py -c 10 -l cn`

This will generate 10 samples using the Chinese dictionary that can be found in
in `dicts/cn.txt`:

![](_static/images/tutorial/2/1.jpg "1")
![](_static/images/tutorial/2/2.jpg "2")
![](_static/images/tutorial/2/3.jpg "3")
![](_static/images/tutorial/2/4.jpg "4")
![](_static/images/tutorial/2/5.jpg "5")
![](_static/images/tutorial/2/6.jpg "6")
![](_static/images/tutorial/2/7.jpg "7")
![](_static/images/tutorial/2/8.jpg "8")
![](_static/images/tutorial/2/9.jpg "9")
![](_static/images/tutorial/2/10.jpg "10")

Since the concept of word in Chinese is a bit trickier, the dictionary is made of single
characters (make your own!). Let's do this again with `-w 5` to get something prettier.

`python3 run.py -c 10 -l cn -w 5`

![](_static/images/tutorial/3/1.jpg "1")
![](_static/images/tutorial/3/2.jpg "2")
![](_static/images/tutorial/3/3.jpg "3")
![](_static/images/tutorial/3/4.jpg "4")
![](_static/images/tutorial/3/5.jpg "5")
![](_static/images/tutorial/3/6.jpg "6")
![](_static/images/tutorial/3/7.jpg "7")
![](_static/images/tutorial/3/8.jpg "8")
![](_static/images/tutorial/3/9.jpg "9")
![](_static/images/tutorial/3/10.jpg "10")

Now that looks better, but what's up with the spacing between the characters? We would rather
have no spaces. Add `-sw 0`.

`python3 run.py -c 10 -l cn -w 5 -sw 0`

![](_static/images/tutorial/4/1.jpg "1")
![](_static/images/tutorial/4/2.jpg "2")
![](_static/images/tutorial/4/3.jpg "3")
![](_static/images/tutorial/4/4.jpg "4")
![](_static/images/tutorial/4/5.jpg "5")
![](_static/images/tutorial/4/6.jpg "6")
![](_static/images/tutorial/4/7.jpg "7")
![](_static/images/tutorial/4/8.jpg "8")
![](_static/images/tutorial/4/9.jpg "9")
![](_static/images/tutorial/4/10.jpg "10")


Asian scripts can be written top to bottom, you might want to
add the `-or 1` argument to get vertical text.

`python3 run.py -c 10 -l cn -w 5 -sw 0 -or 1`

![](_static/images/tutorial/5/1.jpg "1")
![](_static/images/tutorial/5/2.jpg "2")
![](_static/images/tutorial/5/3.jpg "3")
![](_static/images/tutorial/5/4.jpg "4")
![](_static/images/tutorial/5/5.jpg "5")
![](_static/images/tutorial/5/6.jpg "6")
![](_static/images/tutorial/5/7.jpg "7")
![](_static/images/tutorial/5/8.jpg "8")
![](_static/images/tutorial/5/9.jpg "9")
![](_static/images/tutorial/5/10.jpg "10")

You can do much and more with TRDG, if you run into a missing feature, simply [open an issue](https://github.com/Belval/TextRecognitionDataGenerator/issues/new).

## Text distorsions

For those familiar with the process of training a machine learning model, you often have to deal with overfitting, which is
when the model gets too good at predicting the samples in the training data and stops generalizing to unseen examples. One trick
to prevent this is by adding the distorsion to the data.

While TRDG does not dwelve too deeply in augmentations, as many better and more complete [libraries](https://github.com/search?q=image+augmentation)
already take care of it, some operations are available for convenience through the `-d` argument which as 3 possible values:

- 0: None
- 1: Sine wave
- 2: Cosine wave
- 3: Random

`python3 run.py -c 5 -w 5 -d 1`

![](_static/images/tutorial/8/1.jpg "1")
![](_static/images/tutorial/8/2.jpg "2")
![](_static/images/tutorial/8/3.jpg "3")
![](_static/images/tutorial/8/4.jpg "4")
![](_static/images/tutorial/8/5.jpg "5")

`python3 run.py -c 5 -w 5 -d 3`

![](_static/images/tutorial/9/1.jpg "1")
![](_static/images/tutorial/9/2.jpg "2")
![](_static/images/tutorial/9/3.jpg "3")
![](_static/images/tutorial/9/4.jpg "4")
![](_static/images/tutorial/9/5.jpg "5")

## A more advanced use case

Text in the real world is not always black, and most importantly, text in the real
world is almost never straight. What if we want to emulate that?

`python3 run.py -c 10 -k 15 -rk -bl 0.5 -rbl -tc '#000000,#888888'`

Which can be translated to: generate 10 examples with a skewing angle between -15 and
15 with an added gaussian blur between 0 and 0.1. Finally, the text color should be picked randomly
between black and gray (including all the colors inbetween).

Sure enough, the output is much more colourful!

![](_static/images/tutorial/6/1.jpg "1")
![](_static/images/tutorial/6/2.jpg "2")
![](_static/images/tutorial/6/3.jpg "3")
![](_static/images/tutorial/6/4.jpg "4")
![](_static/images/tutorial/6/5.jpg "5")
![](_static/images/tutorial/6/6.jpg "6")
![](_static/images/tutorial/6/7.jpg "7")
![](_static/images/tutorial/6/8.jpg "8")
![](_static/images/tutorial/6/9.jpg "9")
![](_static/images/tutorial/6/10.jpg "10")

The default resolution might be too small to your taste (and I agree). By default the output is 32 pixels high
because it's the height used by most text recognition papers. Now you can change that with `-f 64`.

`python3 run.py -c 10 -k 15 -rk -bl 0.5 -rbl -tc '#000000,#888888' -f 64`

![](_static/images/tutorial/7/1.jpg "1")
![](_static/images/tutorial/7/2.jpg "2")
![](_static/images/tutorial/7/3.jpg "3")
![](_static/images/tutorial/7/4.jpg "4")
![](_static/images/tutorial/7/5.jpg "5")
![](_static/images/tutorial/7/6.jpg "6")
![](_static/images/tutorial/7/7.jpg "7")
![](_static/images/tutorial/7/8.jpg "8")
![](_static/images/tutorial/7/9.jpg "9")
![](_static/images/tutorial/7/10.jpg "10")
