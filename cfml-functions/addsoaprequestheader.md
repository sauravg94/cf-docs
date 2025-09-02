# AddSOAPRequestHeader

### Description

Adds a SOAP header to a web service request before making the request.
### Returns

Nothing.
### Category

XML functions
### Function syntax

```coldfusion
AddSOAPRequestHeader(webservice, namespace, name, value [, mustunderstand])
```
### See also

AddSOAPResponseHeader, GetSOAPRequest, GetSOAPRequestHeader, GetSOAPResponse, GetSOAPResponseHeader,
IsSOAPRequest; Basic web service concepts in the Developing ColdFusion Applications
### History

### Parameters

Parameter
Description
webservice
A web service object as returned from the cfobject tag or the CreateObject function.
namespace
A string that is the namespace for the header.
name
A string that contains the name of the SOAP header in the request.
value
The value for the SOAP header; this can be a CFML XML value.
mustunderstand
Optional. True or False (default). Sets the SOAP mustunderstand value for this header.
### Usage

Used within CFML code by a consumer of a web service before it calls the web service.If you pass XML in the value parameter, ColdFusion ignores the namespace and name parameters. If you require a namespace, define it within the XML itself.
### Example

There are two parts to this example. The first part is the web service CFC that this function (as well as the other ColdFusion SOAP functions) uses to demonstrate its interaction with a web service. To implement the web service for this function, see the example for AddSOAPResponseHeader.Execute the following example as a client to see how the AddSOAPRequestHeader function operates.
```coldfusion
<!--- Note that you might need to modify the URL in the CreateObject function
to match your server and the location of the headerservice.cfc file if it is
different than shown here. Likewise for the cfinvoke tag at the end. --->
<h3>AddSOAPRequestHeader Example</h3>
<cfscript>
// Create the web service object.
ws = CreateObject("webservice", "http://localhost/soapheaders/headerservice.cfc?WSDL");
// Set the username header as a string.
addSOAPRequestHeader(ws, "http://mynamespace/", "username", "tom", false);
// Set the password header as a CFML XML object.
doc = XmlNew();
doc.password = XmlElemNew(doc, "http://mynamespace/", "password");
doc.password.XmlText = "My Voice is my Password";
doc.password.XmlAttributes["xsi:type"] = "xsd:string";
addSOAPRequestHeader(ws, "ignoredNameSpace", "ignoredName", doc);
// Invoke the web service operation.
ret = ws.echo_me("argument");
// Get the first header as an object (string) and as XML.
header = getSOAPResponseHeader(ws, "http://www.tomj.org/myns", "returnheader");
XMLheader = getSOAPResponseHeader(ws, "http://www.tomj.org/myns", "returnheader", true);
// Get the second header as an object (string) and as XML.
header2 =getSOAPResponseHeader(ws, "http://www.tomj.org/myns", "returnheader2");
XMLheader2 = getSOAPResponseHeader(ws, "http://www.tomj.org/myns", "returnheader2", true);
</cfscript>
<hr>
<cfoutput>
Soap Header value: #HTMLCodeFormat(header)#<br>
Soap Header XML value: #HTMLCodeFormat(XMLheader)#<br>
Soap Header 2 value: #HTMLCodeFormat(header2)#<br>
Soap Header 2 XML value: #HTMLCodeFormat(XMLheader2)#<br>
Return value: #HTMLCodeFormat(ret)#<br>
</cfoutput>
<hr>
<cfinvoke component="soapheaders.headerservice" method="echo_me" returnvariable="ret" in_here="hi">
</cfinvoke>
<cfoutput>The cfinvoke tag returned: #ret#</cfoutput>
```
## Get help faster and easier
New user?
Quick links
