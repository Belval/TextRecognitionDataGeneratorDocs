# Tutorial

TextRecognitionDataGenerator comes with an (hopefully) easy to use CLI. The tutorial
is actually multiple tutorials, combined in a single page. Feel free to skip sections
that are not relevant to your use case.

## Just generating data

Fun fact, you don't need to use any command line arguments if you want English data
generated using multiple fonts. Indeed, simply running `python3 run.py` will create
1000 English, single word images in the `out/` directory such as these:

![](_static/images/tutorial/1.jpg "1")
![](_static/images/tutorial/2.jpg "2")
![](_static/images/tutorial/3.jpg "3")
![](_static/images/tutorial/4.jpg "4")
![](_static/images/tutorial/5.jpg "5")
![](_static/images/tutorial/6.jpg "6")
![](_static/images/tutorial/7.jpg "7")
![](_static/images/tutorial/8.jpg "8")
![](_static/images/tutorial/9.jpg "9")
![](_static/images/tutorial/10.jpg "10")
![](_static/images/tutorial/11.jpg "11")
![](_static/images/tutorial/12.jpg "12")

Now maybe 1000 is too many or too few for your usecase. You can add the `-c` argument
to set how many examples will be generated.

`python3 run.py -c 10`

As expected, you will find 10 examples in the `out/` directory.

## Generating Chinese data

This is a common usecase, and one that is easy with TRDG.

`python3 run.py -c 10 -l cn`

This will generate 10 samples, using the Chinese dictionary that can be found in
in `dicts/cn.txt`. Since Asian scripts can be written top to bottom, you might want to
add the `-or 1` argument to get vertical text.

`python3 run.py -c 10 -l cn -or 1`


## A more advanced use case

Text in the real world is not always black, and most importantly, text in the real
world is almost never straight. What if we want to emulate that?

`python3 run.py -c 10 -k 15 -rk -bl 2 -rbl -tc '#FF0000,#00FF00'`

Which can be translated to: generate 10 examples with a skewing angle between -15 and
15 with an added gaussian blur between 0 and 2. Finally, the text color should be picked randomly
between red and green.


