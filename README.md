Stagger
=======

Stagger is an ID3v1/ID3v2 tag manipulation package written in pure Python 3.

The ID3v2 tag format is notorious for its useless specification documents and its quirky, mutually incompatible partial implementations.
Stagger is to provide a robust tagging package that is able to handle all the various badly formatted tags out there and allow you to convert them to a consensus format.
This fork aims to maintain compatibility with recent Python versions.

## Features

- Reads and writes ID3 v1.0, 1.1, 2.2, 2.3 and 2.4 tags
- Supports conversion between tag versions
- Supports unsynchronized tags (all versions) and compressed frames (2.3 and 2.4 only)
- Full Unicode support, with customizable text encoding preferences
- Has built-in support for all standard frame types (plus a few nonstandard ones). Easily extensible with additional frame types if needed
- Supports duplicate frames and multiple text strings in a single frame
- Supports reading/writing frames of unrecognized types and frames with invalid data. Automatically recognizes unknown text and URL frames
- The order of frames in a tag is fully customizable
- Package comes with extensive unit tests for an extra measure of code quality
- Tested under Mac OS X, Windows and GNU/Linux


```pycon
>>> from stagger import read_tag
>>> from stagger.id3 import TIT2                  # Support for all ID3 tags
>>> tag = read_tag("track01.mp3")                 # Read and parse a file
>>> tag[TIT2]                                     # Every tag is a MutableMapping
TIT2(utf-8 "Staralfur")
>>> tag[TIT2] = TIT2(text="The Show Must Go On")  # Explicit constructor
>>> tag[TIT2] = "The Show Must Go On"             # Implicit constructor
>>> tag[TIT2] = ("Foo", "Bar", "Baz")             # Multiple string support
>>> tag.title = "The Battle of Evermore"          # Easy and friendly API
>>> tag.write()                                   # Write changes back to file
```

## Installation

You can add it to your setup.py or pyproject.toml file as a dependency using:

`stagger @ git+https://git@github.com/Jelmerro/stagger@master`

## Tests

You can run the unit tests with:

`python -m unittest test/*.py`

## License

Stagger was first started by Karoly Lorentey, but this fork is developed by Jelmer van Arnhem.
It is licensed under the terms of the BSD license, please see the individual files and the LICENSE for further details.
