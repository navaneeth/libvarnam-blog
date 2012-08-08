---
layout: post
title: "A command line interface to libvarnam"
date: 2012-08-08 16:00
comments: true
categories: [libvarnam, Varnam]
---
I have created a simple command line interface to `libvarnam`. It is called as `varnamc`.

```
$ ./varnamc -h
Usage: varnamc [options] language_code args
    -l, --library FILE               Sets the varnam library
    -v, --verbose                    Enable verbose output
    -t, --transliterate TEXT         Transliterate the given text
    -r, --reverse-transliterate TEXT Reverse transliterate the given text
    -n, --learn [TEXT]               Learn given text. Use --files option together with this to learn from file
    -f, --files files                Reads from the specified files
    -s, --symbols VALUE              Sets the symbols file
    -c, --compile FILE               Compile symbols file
    -d, --output-dir dir             Sets the output directory
    -h, --help                       Display this screen
```

This allows to quickly try out various features of `libvarnam`.

Usage
------
Invoke `varnamc` with a symbols file and one action. Action could be transliterate, reverse-transliterate, compile or learn.

To transliterate the text `malayalam`,

```
$ ./varnamc --symbols ml --transliterate malayalam
```

`--symbols (-s)` specifies which language to use. This can accept either a language code or full path to the symbols file. If language code is specified, `varnamc` search for appropriate symbols file in some predefined search paths.

To learn a word,

```
$ ./varnamc --symbols ml --learn മലയാളം
```

To compile a scheme file,

```
$ ./varnamc --symbols ml --compile schemes/ml-unicode
```

By default, `varnamc` writes the files into the execution directory. This can be changed by specifying `--output-dir` switch.

Have a great day!