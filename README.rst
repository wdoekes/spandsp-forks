Please see one of the branches.

----

Diff between stretch and upstream::

    $ git diff --stat debian-stretch-0.0.6+dfsg-0.1..upstream-0.0.6 --
     debian/changelog                                                   | 214 +++---------------------------------------------
     debian/clean                                                       |   3 -
    ...

Relevant .c and .h file dirs::

    $ find . -name '*.h' -o -name '*.c' | grep -vE './tests/|./test-data/' |
        awk -F/ '{print $2}' | sort -u
    spandsp-sim
    src

Changes between upstream-0.0.6 and debian-stretch::

    $ git diff debian-stretch-0.0.6+dfsg-0.1..upstream-0.0.6 -- spandsp-sim src
    diff --git a/src/spandsp/fast_convert.h b/src/spandsp/fast_convert.h
    index 9652c54..10679ea 100644
    --- a/src/spandsp/fast_convert.h
    +++ b/src/spandsp/fast_convert.h
    @@ -195,7 +195,7 @@ extern "C"
         {
             return (long int) (x);
         }
    -#elif (defined(__ppc__)  ||   defined(__powerpc__)) && !defined(__NO_FPRS__)
    +#elif defined(__ppc__)  ||   defined(__powerpc__)
         static __inline__ long int lfastrint(register double x)
         {
             int res[2];
