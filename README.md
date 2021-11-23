## sendosc
sendosc is a simple command-line tool for sending OSC packet.

## build

Tested on Mac, but should also work on Windows/Linux (TODO).

```
git clone https://github.com/isabelgk/sendosc.git
cd sendosc
git submodule update --init
mkdir build
cd build
cmake ..
cmake --build .
```

## usage
```
sendosc
usage : sendosc dst_host dst_port path [[type] [param]] ...
 
   type
     i : int
     f : float
     b : boolean (true/false)
     s : string
 
   example
     ./sendosc 127.0.0.1 5678 /test1 i 123
     ./sendosc 127.0.0.1 5678 /test2 f 123.45
     ./sendosc 127.0.0.1 5678 /test3 s teststring
     ./sendosc 127.0.0.1 5678 /test4 b true
     ./sendosc 127.0.0.1 5678 /test5 s teststring i 123 f 123.4 b false
```

## Copyright and license
Copyright (c) 2015 yoggy

Copyright (c) 2021 Isabel Kaspriskie

Released under the [MIT license](LICENSE.txt)
