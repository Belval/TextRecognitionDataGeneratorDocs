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
