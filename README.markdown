## OVERVIEW
wwwaiter is a program for visualizing delays in receiving portions of a document from a web server. It won't be exact due to buffering done by your webserver and operating system, but it should help diagnose slow parts of web applications.

## INSTALLATION
wwwaiter requires a reasonably modern perl and the following modules. If you are using linux, these should be available via your distribution's package manager. If not, you can install them via CPAN.

  * Getopt::Std
  * IO::Socket
  * Term::ANSIColor
  * Term::ReadKey
  * Time::HiRes

## USAGE
wwwaiter has two modes of use. In either mode, it shows you the lengths of the delays as it encounters them, the total number of delays and time spent waiting, and the total document load time.

The default mode shows limited context before and after each delay. The default amount of context displayed is 3 lines; this can be changed with the -c option. The verbose mode, specified with -v, shows the entire document and switches the output color after each delay. 

By default, wwwaiter reports on any delay greater than 10 milliseconds. This threshhold can be changed with the -d option.

If the web server you are testing uses a port other than port 80, you can specify it with the -p option.

## EXAMPLES

    $ wwwaiter example.com/foo.html - Display 3 lines before and after each 10 ms delay.
    $ wwwaiter -c 5 -d 100 example.com/foo.html - Display 5 lines before and after each 100 ms delay.
    $ wwwaiter -v example.com/foo.html - Display the entire document and change the color after each 10 ms delay.
    $ wwwaiter -p 8080 example.com/foo.html - Connect to the web server running example.com on port 8080 rather than port 80.

## LIMITATIONS
wwwaiter currently does not understand HTTP response codes. It would be nice if it could follow redirects.

wwwaiter suppresses the output of blank lines. It would be nice if there was an option to disable this feature.

## THANKS
Thanks to openclipart.org user capi_x for releasing the drawing of a snail that wwwaiter uses as its logo into the public domain.
