# Creating a Web Service Type from Tcl #

## Overview ##


Webservice Type declaration is part of the Webservices Utility package.


When writing a web service it is often requried to write a complex type
definition for an argument containing structured data.


When calling an operation on a web service it is sometimes convient to define
a complex type to return structured data as an XML fragment even though the
sevice may state that it is only expecting a string.

## Loading the Webservices Utility Package ##


To load the webservices server package, do:
```
package require WS::Utils
```

This command will only load the utilities the first time it is used, so it
causes no ill effects to put this in each file using the utilties.

## Defining a type ##


**Procedure Name:** _::WS::Utils::ServiceTypeDef_


**Description:** Define a type for a service.


**Arguments:**
  * mode
> > _Client_ or _Server_
  * service
> > The name of the service this type definition is for
  * type
> > The type to be defined/redefined
  * definition
> > The definition of the type's fields.  This consist of one or more occurance of a field definition.  Each field definition consist of:  "fieldName fieldInfo".  Where fieldInfo is: {**type** typeName **comment** commentString}, _typeName_ can be any simple or defined type and\_commentString_is a quoted string describing the field._


**Returns:** Nothing


**Side-Effects:** None


**Exception Conditions:** None


**Pre-requisite Conditions:** None

## Defining a derived type ##


**Procedure Name:** _::WS::Utils::ServiceSimpleTypeDef_


**Description:** Define a derived type for a service.


**Arguments:**
  * mode
> > _Client_ or _Server_
  * service
> > The name of the service this type definition is for
  * type
> > The type to be defined/redefined
  * definitione
> > The definition of the type's fields.  This consist of one or more occurance of a field definition.  Each field definition consist of:  "fieldName fieldInfo"  Where fieldInfo consist of:
      * **baseType** _typeName_ - any simple or defined type.
      * **comment** _commentString_ - a quoted string describing the field.
      * **pattern** _value_
      * **length** _value_
      * **fixed** _"true"|"false"_
      * **maxLength** _value_
      * **minLength** _value_
      * **minInclusive** _value_
      * **maxInclusive** _value_
      * **enumeration** _value_



**Returns:** Nothing


**Side-Effects:** None


**Exception Conditions:** None


**Pre-requisite Conditions:** None


## Getting a type definition ##


**Procedure Name:** _::WS::Utils::GetServiceTypeDef_


**Description:** Query for type definitions.


**Arguments:**
  * mode
> > _Client_ or _Server_
  * service
> > The name of the service this query is for
  * type
> > The type to be retrieved (optional)


**Returns:**

> If type not provided, a dictionary object describing all of the types for the service.  If type provided, a dictionary object describing the type.  A definition consist of a dictionary object with the following key/values:
    * **xns**         - The namespace for this type.
    * **definition**  - The definition of the type's fields.  This consist of one or more occurance of a field definition.  Each field definition consist of:  "fieldName fieldInfo" Where fieldInfo is: {**type** _typeName_ **comment** **commentString**}, _typeName_ can be any simple or defined type and  _commentString_ is a quoted string describing the field.



**Side-Effects:** None


**Exception Conditions:** None


**Pre-requisite Conditions:** The service must be defined.