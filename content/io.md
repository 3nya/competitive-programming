# io

ios_base::sync_with_stdio(false) controls whether or not the C and C++ output
streams (printf and cin) are synced. By default, they're synced, which means you
can mix then without issues and expect them to be output in the right order.
Disabling this means c++ cin has an independent buffer, which speeds up input
but also means you have to take certain things into consideration if you want to
use both styles in the same program

cin.tie(NULL) is another case of disabling buffer sync. By default, cin and cout
are tied, meaning each stream is flushed before an I/O operation from the other.
Disabling this means that you have to manually ensure cout streams are flushed
if your program requires things to be read/output in order (i.e. interactive
problems)

    -- crop science major

[source](https://stackoverflow.com/questions/31162367/significance-of-ios-basesync-with-stdiofalse-cin-tienull)
