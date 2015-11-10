# Web Service Server Side -- Creating a Tcl Web Service #

# Introduction #

The Web Services package, WS::Server, is not a standalone application, but rather is designed be a "module" of [http::/tclhttpd.sf.net TclHttpd]. The following command is normally placed in httpdthread.tcl:


## Loading the Web Services Server Package ##

To load the web services server package, do:

```
 package require WS::Server
```

This command will only load the server the first time it is used, so it causes no ill effects to put this in each file declaring a service or service procedure.

## Defining a Service ##

The code that defines a service is normally placed in one or more files in the custom directory.

**Procedure Name:** ::WS::Server::Service

**Description:** Declare a Web Service, the following URLs will exist

  1. /service/_ServiceName
> > Displays an HTML page describing the service
  1. /service/_ServiceName/wsdl
> > Returns a WSDL describing the service
  1. /service/_ServiceName/op
> > Invoke an operation_

**Arguments:** this procedure uses position independent arguments, they are:

  * -host
> > The host name for this serice. Defaults to "localhost"
  * -description
> > The HTML description for this service
  * -xmlnamespace
> > Extra XML namespaces used by the service
  * -service
> > The service name (this will also be used for the Tcl namespace of the procedures that implement the operations).
  * -premonitor
> > This is a command prefix to be called before an operation is called.  The following arguments are added to the command prefix:
> > > `PRE serviceName operationName operArgList`
  * -postmonitor

> > This is a command prefix to be called after an operation is called.  The following arguments are added to the command prefix:
> > > `POST serviceName operationName OK|ERROR results`
  * -inheaders

> > List of input header types.
  * -outheaders
> > List of output header types.
  * -checkheader
> > Command prefix to check headers. If the call is not to be allowed, this command should raise an error. The signature of the command must be:
```
cmd \
    service \
    operation \
    caller_ipaddr \
    http_header_list \
    soap_header_list
```
  * -mode           - Mode that service is running in.  Must be one of:
> > tclhttpd  -- running inside of tclhttpd or an
> > > evironment that supplies a
> > > compatilbe Url\_PrefixInstall
> > > and Httpd\_ReturnData commands

> > embedded  -- using the ::WS::Embedded package
> > aolserver -- using the ::WS::AolServer package
> > wub       -- using the ::WS::Wub package
> > rivet     -- running inside Rivet
  * -ports          - List of ports for embedded mode. Default: 80
> > NOTE -- a call should be to
> > > ::WS::Embedded::Listen for each port
> > > in this list prior to this call
  * -traceEnabled   - Boolean to enable/disable trace being passed back in exception

> > Defaults to "Y"

**Returns:** Nothing

**Side-Effects:** None

**Exception Conditions:**

  * MISSREQARG
> > Missing required arguments

**Pre-requisite Conditions:** None


## Defining an Operation (aka a Service Procedure) ##

**Procedure Name:** ::WS::Server::ServiceProc

**Description:** Register an operation for a service and declare the procedure to handle the operations.

**Arguments:**

  * ServiceName
> > Name of the service this operation is for
  * NameInfo
> > List of three elements:
    1. OperationName -- the name of the operation
    1. ReturnType    -- the type of the procedure return, this can be a simple or complex type
    1. Description   -- description of the return method
  * Arglist
> > List of argument definitions, each list element must be of the form:
    1. ArgumentName -- the name of the argument
    1. ArgumentTypeInfo -- A list of:
```
{type typeName comment commentString} 
```

> where _typeName_ can be any simple or defined type and _commentString_ is a quoted string describing the field
  * Documentation
> > HTML describing what this operation does
  * Body
> > The tcl code to be called when the operation is invoked. This code should return a dictionary with _OperationName\_Result as a key and the operation's result as the value._

**Returns:** Nothing

**Side-Effects:**

  1. A proceedure named **ServiceName::OperationName** defined
  1. A type name with the name **OperationNameResult** is defined.

**Exception Conditions:** None

**Pre-requisite Conditions:** ::WS::Server::Server must have been called for the ServiceName


## Declaring Complex Types ##

See: [Creating a Web Service Type from Tcl](WStypes.md)