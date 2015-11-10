# Project has moved #

The project has moved to http://core.tcl.tk/tclws/ and is now a Fossil repository.

This site will be maintained as a historic archive.


# Web Services for Tcl #
## Summary ##

The distribution provides both client side access to Web Services and server side creation of Web Services. Currently only document/literal and rpc/encoded with HTTP Soap transport are supported on the client side. The server side currently works with several web servers(see below).  It provides all services as document/literal over HTTP Soap transport. Documentation for the package, including examples can be found here. The distribution consist ofseveral packages

## Documentation ##

  1. [Client Side](WSClient.md)
  1. [Server Side](WSServer.md)
  1. [Defining Types](WSTypes.md)
  1. [An Example](Example.md)

The client is known to work with several [providers](https://code.google.com/p/tclws/wiki/ClientCompatibilityWithServerSide) of  Web Services (your mileage may very).

## Web Servers ##
> The server side works with the following web servers:
    1. [TclHttpd](http://tclhttpd.sourceforge.net/)
    1. [Rivet](http://tcl.apache.org/rivet)
    1. [AOLserver](http://www.aolserver.com)
    1. [WUB](http://code.google.com/p/wub/)
    1. [wibble](http://wiki.tcl.tk/23626)
    1. Embedded mode

## Download ##

A ZIP file for downloading is available [here](http://code.google.com/p/tclws/downloads/list).


## License ##

Standard BSD.


## Packages Required ##

The following packages are used:

  * [Tcl 8.5](http://tcl.sf.net/)
  * [tdom 0.8.1](http://www.tdom.org)
  * [tls](http://tls.sf.net)
  * log from [TclLib](http://tcllib.sf.net/)
  * uri from [TclLib](http://tcllib.sf.net/)
  * http from [Tcl](http://tcl.sf.net/) itself

Additionally, if you are running the [TclHttpd](http://tclhttpd.sourceforge.net/) on Windows, it is highly recommended that you use the [iocpsock](http://sourceforge.net/projects/iocpsock) extension.