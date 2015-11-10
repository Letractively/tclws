# Introduction #

tclws aims to be a standards compliant SOAP server compatible with any modern SOAP client that supports Document/Literal wrapped services.


# Tested clients #

The following clients are known to successfully work with tclws ServerSide:
  * Microsoft C# .NET/CLR; Visual Studio 2003, 2005, 2008, 2010
  * PHP builtin Soap Client -- http://php.net/SoapClient
  * PHP NuSOAP -- http://nusoap.sourceforge.net/
  * Perl CPAN SOAP::WSDL -- http://search.cpan.org/dist/SOAP-WSDL/
  * Perl CPAN SOAP::Lite, however the "stubmaker.pl" utility and the SOAP::Lite WSDL support cannot be used. -- http://search.cpan.org/dist/SOAP-Lite/
  * Java Apache Axis1 -- http://ws.apache.org/axis/
  * Java Apache Axis2 -- http://ws.apache.org/axis2/
  * Tcl tclws -- this project, of course!
  * Python SOAPpy -- http://pywebsvcs.sourceforge.net/
  * Python SUDS -- http://fedorahosted.org/suds/
  * Ruby soap4r -- http://dev.ctor.org/soap4r
  * Ruby savon gem -- http://savon.rubiii.com/

If you have tested any other third-party clients, please feel free to add your successes or failures.