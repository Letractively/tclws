Future plans for the Web Services for Tcl package

# Schedule #

## Q2 2011 -- Release 2.0.0 ##

### Server Side Enhancements ###
  * Declaration of fault codes with complex data types

### Client Side Enhancements ###
  * Processing of fault codes with complex data types


## February 2011 -- Release 1.3.0 ##

Special thanks to Andy Goth and Tom Madilo for their work on the wibble and AOLServer sections.

### Server Side Enhancements ###
  * Works with wibble
  * Improved implementation and examples for AOLServer

## November 2010 -- Release 1.2.0 ##

Thanks to all those who contributed code, especially code to make the WS::Server work inside of servers other than TclHttpd.

### General Side Enhancements ###
  * Support of options to control XML generation (see Using Web Service Options documentation)
  * Documentation enhancements
  * Examples servers for TclHttpd and WUB

### Server Side Enhancements ###
  * Works with WUB
  * Works with AOLServer
  * Works with Rivet
  * Works embedded in an event driven application
  * Generated documentation XHTML compliant

### Client Side Enhancements ###
  * Addition of XML transformations call outs to facilitate signing and general XML processing

## Release 3.0 - wish list ##
  * WSDL 2.0 support
  * Support for the same type name being defined differently in different name spaces.
  * Release date -- dependent on time and demands
(Can be done sooner if work is contributed or paid work requires WSDL 2.0)

# Experimental/Unsupported #
  * Client side REST building tools (see ::WS::Client::CreateService and ::WS::Client::DefineRestMethod)

# Known Bugs #
  * [Issue #18](https://code.google.com/p/tclws/issues/detail?id=#18) - Does not support  the same type name being defined differently in different name space

# Limitations #
  * Supports only "Request-response" Message Exchange Pattern.
  * [Issue #19](https://code.google.com/p/tclws/issues/detail?id=#19) - Does not support UNIONs directly -- requires code (see ::WS::Utils::MutableTypeDef)
  * [Issue #20](https://code.google.com/p/tclws/issues/detail?id=#20) - Only supports WSDL 1.0 and 1.1

# To Do #
  * Add test plans
  * Enhance documentation
  * Add more complex examples