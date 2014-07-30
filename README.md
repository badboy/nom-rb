# nom

**nom** is a command line program that helps you lose weight by tracking your energy intake and creating a negative feedback loop. It's inspired by John Walker's [The Hacker's Diet](https://www.fourmilab.ch/hackdiet/) and tries to automate things as much as possible.

# Setup

Install the `nokogiri` gem:

    $ gem install nokogiri

Then clone this repository, and put the `nom` executable in your `PATH`.

When you run `nom` for the first time, it will ask for your current and your desired weight, as well as a target "weight loss per week" (0.5 is a good value). Finally, it will ask for an SVG viewer (I use `eog -f`, browsers like `firefox` or `chromium` also work).

# Basics

`nom` operates on three files in the directory `~/.nom/`: `config` contains configuration settings, `input` contains stuff you ate, `weight` contains weight measurements. You can edit them by hand.

By default, energy quantities will have the unit "kcal". You can change this by adding a line like `unit: 0.239` to your `~/.nom/config`, which means you want to use the unit "0.239 kcal" (= "1 kJ"). Energy quantities are displayed in parentheses: `(42)`

Weight quantities are displayed as "kg", but you can use arbitrary units, like pounds.

# Usage

Enter `nom help` if you're lost:

    $ nom help
    Available subcommands:
          status                      Display a short food log
       w, weight <weight>             Report a weight measurement
       s, search <term>               Search for a food item in the web
       n, nom <description> <energy>  Report that you ate something
       p, plot                        Plot a weight/intake graph
       l, log                         Display the full food log
       g, grep <term>                 Search in the food log
       e, edit                        Edit the input file
      ew, editw                       Edit the weight file
          help                        Print this help
    There are some useful defaults:
          (no arguments)              status
          <number>                    weight <number>
          <term>                      search <term>
          <term> <number>             nom <term> <number>

So, call `nom` without arguments to get a summary of your current status:

    $ nom
    5.3 kg down (34%), 10.3 kg to go!

    Today: (1774)

       (200) Griespudding
       (110) Graubrot
       (125) Käse
        (87) Orangensaft
    ---------------------
      (1252) remaining

You ate/drank something? Look up at FDDB how much energy it contained. (The search is German only for now, sorry.)

    $ nom Mate
    Club Mate (Brauerei Loscher)
        (40) 1 Glas (200 ml)
        (66) 1 kleine Flasche (330 ml)
        (100) 1 Flasche (500 ml)
    Mate Tee, Figurfit (Bad Heilbrunner)
        (0) 1 Beutel (2 ml)
        (1) 100 g (100 ml)
    Mate Tee, Orange (Bad Heilbrunner)
        (2) 1 Glas (200 ml)
        (0) 15 Filterbeutel (1 ml)
    Mate Tee, Guarana (Bad Heilbrunner)
        (0) 1 Glas (200 ml)
    Club-Mate Cola (Brauerei Loscher)
        (99) 1 Flasche (330 ml)
        (60) 1 Glas (200 ml)

Report your energy intake:

    $ nom Club-Mate 100

Enter your weight regularly:

    $ nom 78.2

And get nice graphs:

    $ nom plot

## License: GPLv2+

*nom* is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 2 of the License, or (at your option) any later version.
