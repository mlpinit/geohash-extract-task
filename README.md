Geohash Extract Task
====================

Note that you need to install [libgeohash](https://github.com/simplegeo/libgeohash) as a
shared library. When checking out libgeohash, modify the Makefile to be:

```
  all: library test

  library:
          gcc -c -Wall -Werror -fpic geohash.c
          gcc -shared -o libgeohash.so geohash.o

  test:
          gcc geohash_test.c geohash.c
          ./a.out
          rm a.out

  clean:
          rm -rf *.a *.o *.so
```

(Note that configuration works for Linux systems. Check out [this post](http://stackoverflow.com/questions/10021428/macos-how-to-link-a-dynamic-library-with-a-relative-path-using-gcc-ld) on StackOverflow to see what the configuration ought to be for OSX).

After that, run `make` to create the library. When running the extract script, make sure to
run it like `LD_LIBRAR_PATH=/path/to/libgeohash` so that FFI can link the shared library appropriately.

Good luck!
