# simplesite-example

Author: Adam Beagle

## Description

This repository demonstrates a minimal example site built using the [Python static site generator `simplesite`](https://github.com/adambeagle/simplesite). It is ideal for use as a starting point for a new site.

## Requirements

* python 3.2+
* `simplesite` package (see Getting Started below for installation instructions

## Getting Started

1. Install `simplesite` and dependencies

    1. Clone `simplesite` with `git clone https://github.com/adambeagle/simplesite.git` into the directory of your choice.
    1. Navigate to the new `simplesite` directory and run `pip install .`
    1. Get dependencies with `pip install -r requirements.txt`

1. Clone this repo with `git clone https://github.com/adambeagle/simplesite-example.git`

1. Navigate to the `simplesite-example` directory within this repo and run `python simplesiteexample.py` to generate the site, which will be written in the `output/` directory by default.

1. View the site in a browser by running `python simplesiteexample.py --server` (which also re-generates the site). By default this will make the site available at `localhost:8000`.

## Usage

Be sure to read through the [simplesite documentation](https://github.com/adambeagle/simplesite/blob/master/README.md) to get a feel for how it works.

By default, invoking `python simplesiteexample.py` generates and writes the site with the default URL system (relative).

### Command line options

There are several optional command line arguments for `simplesiteexample.py`:

* -s, --server
    
    Runs a `python.http` `SimpleHttpServer` at the output root that serves the site so it may be viewed in development. The port and address binding of the server may be set with the options below. This is essentially equivalent to running `python -m http.server` in the root output directory, but saves the step of manually navigating to it.
    
    If this flag is not present, the site is only generated and no server is run.
    
* -p, --port [int]

    Set the port the server will listen on. Does nothing if the `-s` flag is not also present. Defaults to 8000. To change default, change `DEFAULT_PORT` in `simplesiteexample.py`.

* -b, --bind [address]

    Set the address the server will bind to. Does nothing if the `-s` flag is not also present. Defaults to empty, which equates to `0.0.0.0`.

* -u, --urls [relative | abs_production | abs_local]

    Specify the URL system to use when generating the site. See `URL_OPTIONS` in `simplesiteexample.py`.
    
    This allows templates to write URLs in the form `{{ site_url }}some/address/`, and have the resulting URLs match the chosen system.
    
    * `relative` - The example above would be rendered as `/some/address/`
    * `abs_local` - URLs are rendered as absolute paths to the file on the filesystem. On a UNIX system, the example above might be rendered as `/home/username/simplesite-example/simplesite-example/output/some/address/`. In general, if using the server, this option is not useful, even in development. Use `relative` instead.
    * `abs_production` - By default, the example above would be rendered as `http://your-site-here.com/some/address/`. To change the default site url, change the value for `abs_production` in `URL_OPTIONS`, near the top of `simplesiteexample.py`.

### runserver

A `runserver` script is provided for Linux systems that runs a server much in the same way as setting the `-s` flag, but also automatically binds to an address visible on the LAN rather than `localhost`.

## Other Demos

The [`landonhotel` repository](https://github.com/adambeagle/landonhotel) is a larger, more fully-formed and practical site making use of `simplesite`.
