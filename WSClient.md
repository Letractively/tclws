# Web Service Client Side -- Calling Web Services from Tcl #

# Introduction #

The Web Services Client package provides a several ways to define what operations a remote Web Services Server provides and how to call those operations. It also includes several ways to call an operation.

The following ways are provided to define remote operations:

  * Loading a pre-parsed WSDL
  * Querying a remote Web Services Server for its WSDL and parsing it
  * Parsing a saved WSDL

The parsed format is much more compact than the XML of a WSDL.

The following ways are provided to directly call an operation of a Web Service Server:

  * Synchronous Call returning a dictionary object
  * Synchronous Call returning the raw XML
  * Asynchronous Call with separate success and error callbacks
  * Creation of stub Tcl procedures to make synchronous calls


# Details #

## Loading the Web Services Client Package ##

To load the web services server package, do:

```
 package require WS::Client
```

This command will only load the client code the first time it is used, so it causes no ill effects to put this in each file using the client procedures.


## Querying a remote Web Services Server for its WSDL and parsing it ##

**Procedure Name:** ::WS::Client::GetAndParseWsdl

**Arguments:**

  * url
> > The url of the WSDL
  * headers
> > Extra headers to add to the HTTP request. This is a key value list argument. It must be a list with an even number of elements that alternate between keys and values. The keys become header field names. Newlines are stripped from the values so the header cannot be corrupted. This is an optional argument and defaults to {}.
  * serviceAlias
> > Alias (unique) name for service. This is an optional argument and defaults to the name of the service in serviceInfo.

**Returns:** The parsed service definition.  This can be cached to the local file system and used in subsequent executions of the application via _::WS::Client::LoadParsedWsdl_

**Side-Effects:** None

**Exception Conditions:** None

**Pre-requisite Conditions:** None


## Parsing a saved WSDL ##

**Procedure Name:** ::WS::Client::ParseWsdl

**Description:** Parse a WSDL

**Arguments:**

  * wsdlXML - XML of the WSDL

**Optional Arguments:**

  * -createStubs 0|1
> > create stub routines for the service NOTE -- Webservice arguments are position independent, thus the proc arguments will be defined in alphabetical order.
  * -headers
> > Extra headers to add to the HTTP request. This is a key value list argument. It must be a list with an even number of elements that alternate between keys and values. The keys become header field names. Newlines are stripped from the values so the header cannot be corrupted. This is an optional argument and defaults to {}.
  * -serviceAlias
> > Alias (unique) name for service. This is an optional argument and defaults to the name of the service in serviceInfo.

**Returns:** The parsed service definition

**Side-Effects:** None

**Exception Conditions:**None

**Pre-requisite Conditions:** None


## Loading a pre-parsed WSDL ##

**Procedure Name:** ::WS::Client::LoadParsedWsdl

**Description:** Load a saved service definition in

**Arguments:**

  * serviceInfo
> > parsed service definition, as returned from ::WS::Client::ParseWsdl or ::WS::Client::GetAndParseWsdl
  * headers
> > Extra headers to add to the HTTP request. This is a key value list argument. It must be a list with an even number of elements that alternate between keys and values. The keys become header field names. Newlines are stripped from the values so the header cannot be corrupted. This is an optional argument and defaults to {}.
  * serviceAlias
> > Alias (unique) name for service. This is an optional argument and defaults to the name of the service in serviceInfo.

**Returns:** The name of the service loaded

**Side-Effects:** None

**Exception Conditions:** None

**Pre-requisite Conditions:** None


## Synchronous Call returning a dictionary object ##

**Procedure Name:** ::WS::Client::DoCall

**Description:** Call an operation of a web service

**Arguments:**

  * serviceName
> > The name of the Webservice
  * operationName
> > The name of the Operation to call
  * argList
> > The arguements to the operation as a dictionary object This is for both the Soap Header and Body messages.
  * headers
> > Extra headers to add to the HTTP request. This is a key value list argument. It must be a list with an even number of elements that alternate between keys and values. The keys become header field names. Newlines are stripped from the values so the header cannot be corrupted. This is an optional argument and defaults to {}.

**Returns:**


> The return value of the operation as a dictionary object. This includes both the return result and any return headers.


**Side-Effects:** None

**Exception Conditions:**

  * WSCLIENT HTTPERROR
> > if an HTTP error occured
  * others
> > as raised by called Operation

**Pre-requisite Conditions:** Service must have been defined.

## Asynchronous Call with separate success and error callbacks ##

**Procedure Name:** ::WS::Client::DoAsyncCall

**Description:** Call an operation of a web service asynchronously

**Arguments:**

  * serviceName
> > The name of the Webservice
  * operationName
> > The name of the Operation to call
  * argList
> > The arguements to the operation as a dictionary object This is for both the Soap Header and Body messages.
  * succesCmd
> > A command prefix to be called if the operations does not raise an error.  The results, as a dictionary object are concatinated to the prefix. This includes both the return result and any return headers.

  * errorCmd
> > A command prefix to be called if the operations raises an error.  The error code and stack trace are concatinated to the prefix.
  * headers
> > Extra headers to add to the HTTP request. This is a key value list argument. It must be a list with an even number of elements that alternate between keys and values. The keys become header field names. Newlines are stripped from the values so the header cannot be corrupted. This is an optional argument and defaults to {}.

**Returns:** Nothing.

**Side-Effects:** None

**Exception Conditions:**

  * WSCLIENT HTTPERROR
> > if an HTTP error occured
  * others
> > as raised by called Operation

**Pre-requisite Conditions:** Service must have been defined.

## Creation of stub Tcl procedures to make synchronous calls ##

**Procedure Name:** ::WS::Client::CreateStubs

**Description:** Create stubs routines to make calls to Webservice Operations.

All routines will be create in a namespace that is the same as the service name.  The procedure name will be the same as the operation name.

NOTE -- Webservice arguments are position independent, thus the proc arguments will be defined in alphabetical order.

**Arguments:**

  * serviceName
> > The service to create stubs for

**Returns:** A string describing the created procedures.

**Side-Effects:** Existing namespace is deleted.

**Exception Conditions:** None

**Pre-requisite Conditions:** Service must have been defined.


## Synchronous Call returning the raw XML ##

**Procedure Name:** ::WS::Client::DoRawCall

**Description:** Call an operation of a web service

**Arguments:**

  * serviceName
> > The name of the Webservice
  * operationName
> > The name of the Operation to call
  * argList
> > The arguements to the operation as a dictionary object This is for both the Soap Header and Body messages.
  * headers
> > Extra headers to add to the HTTP request. This is a key value list argument. It must be a list with an even number of elements that alternate between keys and values. The keys become header field names. Newlines are stripped from the values so the header cannot be corrupted. This is an optional argument and defaults to {}.

**Returns:**

The XML of the operation.

**Side-Effects:** None

**Exception Conditions:**

  * WSCLIENT HTTPERROR
> > if an HTTP error occured

**Pre-requisite Conditions:** Service must have been defined.