# NAME

Compress::Snappy - (de)compress data in Google's Snappy compression format

# SYNOPSIS

```perl6
my Buf $compressed = Compress::Snappy::compress("hello, world");
my Bool $valid = Compress::Snappy::validate($compressed);
my Buf $decompressed = Compress::Snappy::decompress($compressed);
```

See also examples/test.p6

# DESCRIPTION

This module uses NativeCall to provide bindings to the C API for libsnappy, a
compression library with an emphasis on speed over compression.

Snappy must be installed in order to use this package. Depending on your OS, installation instructions are as follows:

- Windows

Download Snappy from https://snappy.machinezoo.com/downloads/ and follow the instructions.

- OS X
```
$ brew install snappy
```

- Ubuntu/Debian
```
$ sudo apt-get install snappy
```

- OpenSUSE
```
$ sudo zypper install snappy
```

- Fedora
```
$ sudo yum install snappy
```

- Arch/Manjaro
```
$ sudo pacman -S snappy
```

- FreeBSD
```
# pkg install snappy
```

or

```
# cd /usr/ports/archiver/snappy
# make config
# make
# make install
```

- OpenBSD
```
$ doas pkg_add snappy
```

or

```
$ cd /usr/ports/archivers/snappy
$ doas make
$ doas make install
```

- NetBSD
```
# pkgin install snappy
```

or

```
# cd /usr/pkgsrc/devel/snappy
# make
# make install
```

# FUNCTIONS

## Compress::Snappy::compress(Blob $uncompressed) returns Buf

Main compression function. Returns a Buf of compressed data.

## Compress::Snappy::compress(Str $uncompressed, Str $encoding = 'utf-8') returns Buf

Convenience function to make a Str to an encoded Blob and compress that.
Encoding defaults to utf-8 if not specified.

## Compress::Snappy::decompress(Blob $compressed, Str $encoding)

Decompress provided data to a Buf.  If an optional $encoding is
specified, will decode the Buf and return a Str instead.

## Compress::Snappy::validate(Blob $compressed) returns Bool

Returns if the compressed data is valid, without fully decompressing it.

# SEE ALSO

[Snappy on Google Code](https://code.google.com/p/snappy/)

[Snappy on GitHub](https://github.com/google/snappy)
