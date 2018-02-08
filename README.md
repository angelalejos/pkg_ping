# pkg_ping
determines and prints the fastest OpenBSD mirror for your version and architecture into the /etc/installurl file.
compiler optimization for speed is not necessary as the calls using ftp will take up the vast majority of the run-time.
privilege separation and pledge are used. This program works on OpenBSD 6.1 and the current 6.2 version as of this writing.

It uses several commandline options including 3 additional levels of verbosity -v, -vv, -vvv. It will search for only non-USA 
mirrors for export encryption compliance if you are searching from outside of the USA with -u. It will accept floating-point
timeout like 1.5 seconds for downloading a small SHA256 file with "-s 1.5" and it will print the options with -h. these options 
can be mixed and  matched as well.

The "-i" option will also choose http and ftp mirrors, where the ftp mirrors are turned into http mirror listings and duplicates
are pruned. between them the http/ftp mirrors are faster than the https mirror selections.

Running as the superuser is prohibited. running the command shown at the end of program execution as root will install the mirror.

"pkg_ping -vs1.5 -ivuv"


It will shortent the timeout period to the currently fastest download time if no -v are used.

clang pkg_ping.c -o pkg_ping
