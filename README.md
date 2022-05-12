# lice-tddschn

Fork of [Lice](https://github.com/licenses/lice), [original license](LICENSE-orig).

lice-tddschn is made faster by not importing the large `pkg_resources` module.

Lice generates license files. No more hunting down licenses from other
projects.

- [lice-tddschn](#lice-tddschn)
  - [Installation](#installation)
    - [pipx](#pipx)
    - [pip](#pip)
  - [Overview](#overview)
  - [I want XXXXXXXXX license in here!](#i-want-xxxxxxxxx-license-in-here)
  - [Usage](#usage)
  - [Develop](#develop)

## Installation

### pipx

This is the recommended installation method.

```
$ pipx install lice-tddschn
```

### [pip](https://pypi.org/project/lice-tddschn/)

```
$ pip install lice-tddschn
```

## Overview

Generate a BSD-3 license, the default:

    $ lice
    Copyright (c) 2013, Jeremy Carbaugh

    All rights reserved.

    Redistribution and use in source and binary forms, with or without modification,
    ...

Generate an MIT license:

    $ lice mit
    The MIT License (MIT)
    Copyright (c) 2013 Jeremy Carbaugh

    Permission is hereby granted, free of charge, to any person obtaining a copy
    ...

Generate a BSD-3 license, specifying the year and organization to be
used:

    $ lice -y 2012 -o "Sunlight Foundation"
    Copyright (c) 2012, Sunlight Foundation

    All rights reserved.

    Redistribution and use in source and binary forms, with or without modification,
    ...

Generate a BSD-3 license, formatted for python source file:

    $ lice -l py

    # Copyright (c) 2012, Sunlight Foundation
    #
    # All rights reserved.
    #
    # Redistribution and use in source and binary forms, with or without modification,
    ...

Generate a python source file with a BSD-3 license commented in the
header:

    $ lice -l py -f test
    $ ls
    test.py
    $ cat test.py

    # Copyright (c) 2012, Sunlight Foundation
    #
    # All rights reserved.
    #
    # Redistribution and use in source and binary forms, with or without modification,
    ...

Generate a source file (language detected by -f extension):

    $ lice -f test.c && cat test.c
    /*
     * Copyright (c) 2012, Sunlight Foundation
     *
     * All rights reserved.
     *
     * Redistribution and use in source and binary forms, with or without modification,
    ...

If organization is not specified, lice will first attempt to use <span
class="title-ref">git config</span> to find your name. If not found, it
will use the value of the $USER environment variable. If the project
name is not specified, the name of the current directory is used. Year
will default to the current year.

You can see what variables are available to you for any of the licenses:

    $ lice --vars mit
    The mit license template contains the following variables:
      year
      organization

## I want XXXXXXXXX license in here!

Great! Is it a license that is commonly used? If so, open an issue or,
if you are feeling generous, fork and submit a pull request.

## Usage

    usage: lice [-h] [-o ORGANIZATION] [-p PROJECT] [-t TEMPLATE_PATH] [-y YEAR]
                [--vars] [license]

    positional arguments:
      license               the license to generate, one of: agpl3, apache, bsd2,
                            bsd3, cddl, cc0, epl, gpl2, gpl3, lgpl, mit, mpl

    optional arguments:
      -h, --help            show this help message and exit
      -o ORGANIZATION, --org ORGANIZATION
                            organization, defaults to .gitconfig or
                            os.environ["USER"]
      -p PROJECT, --proj PROJECT
                            name of project, defaults to name of current directory
      -t TEMPLATE_PATH, --template TEMPLATE_PATH
                            path to license template file
      -y YEAR, --year YEAR  copyright year
      -l LANGUAGE, --language LANGUAGE
                            format output for language source file, one of: js, f,
                            css, c, m, java, py, cc, h, html, lua, erl, rb, sh,
                            f90, hpp, cpp, pl, txt [default is not formatted (txt)]
      -f OFILE, --file OFILE Name of the output source file (with -l, extension can be omitted)
      --vars                list template variables for specified license

## Develop

```
$ git clone https://github.com/tddschn/lice-tddschn.git
$ cd lice-tddschn
$ poetry install
```