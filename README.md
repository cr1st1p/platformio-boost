# C++ Boost Libraries inside platformio 

## About
This is just a package  for [platformio](https://platformio.org/) to enable you to use parts from the C++ [Boost](https://www.boost.org/) libraries.

Boost requires a working C++ compiler.

Boost is normally created to work on desktop systems. But **some** of the **header only** libraries can work also on embedded systems.

Be aware that Boost was not created specifically for embedded systems (with memory and cpu constraints), so use with care.

## Specific platform information

### Arduino on ESP8266

#### Too many defines
First, Arduino code is doing way too many `#define`s. Some of them are overwriting functions from different namespaces (like `std`) and some of them are so short that they can  overwrite a lot of things.

Non exhaustive list:
- F
- max
- abs
- B1

You should load `Arduino.h` and after that, do some `#undef`s. Especially the *`F`* (flash stored strings) define  can hit you hard.

I'll try to provide in the future a library for helping you with these.

#### Working classes/libraries
What worked (non exhaustive list, based on my current needs):
- boost::string_view
- boost::circular_buffer
- boost::optional
- boost::system::error_code
- boost::variant - https://www.boost.org/doc/libs/1_71_0/doc/html/variant.html
- boost::msm - [Meta State Machine](https://www.boost.org/doc/libs/1_71_0/libs/msm/doc/HTML/index.html) - which means also [boost::mpl](https://www.boost.org/doc/libs/1_71_0/libs/mpl/doc/index.html)



