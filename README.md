**wego** is a weather client for the terminal.

![Screenshots](http://schachmat.github.io/wego/wego.gif)

## Features

* show forecast for 1 to 7 days
* nice ASCII art icons
* displayed info (metric or imperial units):
  * temperature range ([felt](https://en.wikipedia.org/wiki/Wind_chill) and measured)
  * windspeed and direction
  * viewing distance
  * precipitation amount and probability
* ssl, so the NSA has a harder time learning where you live or plan to go
* multi language support
* config file for default location which can be overridden by commandline
* Automatic config management with [ingo](https://github.com/schachmat/ingo)

## Dependencies

* A [working](https://golang.org/doc/install#testing) [Go](https://golang.org/)
  [1.5](https://golang.org/doc/go1.5) environment (You can use
  [goenv](https://github.com/pwoolcoc/goenv) if your distribution does not
  support Go 1.5 yet)
  * In Ubuntu, this is a straightforward: `sudo apt install golang-go`
* utf-8 terminal with 256 colors
* A sane monospaced font containing all the required runes (I use `dejavu sans
  mono`)
* An API key for the backend (see Setup below)

## Installation

* Since recent go versions do not have a , it can be manually set with `export GOPATH="$HOME/go"`
* The, to install or update the wego binary into your `$GOPATH`, run:
```shell
go get -u github.com/alexander0042/wego
```
* Wego can then be launched with `~/go/bin/wego`!

## Setup

0. Run `~/go/bin/wego` once. You will get an error message, but the `.wegorc` config file
   will be generated in your `$HOME` directory (it will be hidden in some file
   managers due to the filename starting with a dot).
0. __With a [forecast.io](http://forecast.io/) account__ (new default)
    * Create your account on https://developer.forecast.io/register
    * Update the following `.wegorc` config variables to fit your needs:
    ```
      backend=forecast.io
      location=40.748,-73.985
      forecast-api-key=YOUR_FORECAST.IO_API_KEY_HERE
    ```
0. __With an [Openweathermap](https://home.openweathermap.org/) account__
    * You can create an account and get a free API key by [signing up](https://home.openweathermap.org/users/sign_up)
    * Update the following `.wegorc` config variables to fit your needs:
    ```
      backend=openweathermap
      location=New York
      owm-api-key=YOUR_OPENWEATHERMAP_API_KEY_HERE
    ```
0. __With a [Worldweatheronline](http://www.worldweatheronline.com/) account__
    * Worldweatheronline no longer gives out free API keys. [#83](https://github.com/alienscience/wego/issues/83)
    * Update the following `.wegorc` config variables to fit your needs:
    ```
      backend=worldweatheronline
      location=New York
      wwo-api-key=YOUR_WORLDWEATHERONLINE_API_KEY_HERE
    ```
0. __With a [pirateweather.net](https://pirateweather.net/) account__
    * Create your account on https://pirateweather.net
    * Update the following `.wegorc` config variables to fit your needs:
    ```
      backend=pirateweather
      location=40.748,-73.985
      forecast-api-key=PIRATEWEATHER.NET_API_KEY_HERE
    ```
0. You may want to adjust other preferences like `days`, `units` and `…-lang` as
   well. Save the file.
0. Run `~/go/bin/wego` once again and you should get the weather forecast for the current
   and next few days for your chosen location.
0. If you're visiting someone in e.g. London over the weekend, just run `wego 4
   London` or `wego London 4` (the ordering of arguments makes no difference) to
   get the forecast for the current and the next 3 days. Unfortunately that does
   not currently work with the forecast.io backend, as it only supports
   latitude,longitude location specification.

You can set the `$WEGORC` environment variable to override the default config
file location.

## License - ISC

Copyright (c) 2014-2017,  <teichm@in.tum.de>

Permission to use, copy, modify, and/or distribute this software for any purpose
with or without fee is hereby granted, provided that the above copyright notice
and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH
REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND
FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT,
INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS
OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER
TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF
THIS SOFTWARE.
