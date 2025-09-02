# AddSOAPResponseHeader

### Description

Adds a SOAP response header to a web service response. Call only from within a CFC web service function that is processing a request as a SOAP web service.
### Returns

Nothing
### Category

XML functions
### Function syntax

AddSOAPResponseHeader(namespace, name, value [, mustunderstand])
### See also

AddSOAPRequestHeader, GetSOAPRequest, GetSOAPRequestHeader, GetSOAPResponse, GetSOAPResponseHeader,
IsSOAPRequest; Basic web service concepts in the Developing ColdFusion Applications
### History

### Parameters

Parameter
Description
namespace
A string that is the namespace for the header.
name
A string that contains the name of the SOAP header in the request.
value
The value for the SOAP header; this can be a CFML XML value.
mustunderstand
### Usage

Call this function only from within a CFC web service function. It throws an error if it is invoked in a context that is not a web service request.If you pass XML in the value parameter, ColdFusion ignores the namespace and name parameters. If you require a namespace, define it within the XML itself.Use the IsSOAPRequest function to determine if the CFC is running as a web service.
### Example

This example creates a CFC web service that illustrates the operation of the AddSOAPResponseHeader function and also provides a web service that illustrates the operation of other ColdFusion SOAP functions. Save the following code as headerservice.cfc in a folder called soapheaders under your web root. Test its operation, and specifically the operation of the AddSOAPResponseHeader function, by executing the examples that invoke this web service. For example, see the example for AddSOAPRequestHeader.
```coldfusion
<h3>AddSOAPResponseHeader Example</h3>
<!--- The headerservice.cfc CFC Web Service.--->
<cfcomponent displayName="tester" hint="Test for SOAP headers">
<cffunction name="echo_me"
access="remote"
output="false"
returntype="string"
displayname="Echo Test" hint="Header test">
<cfargument name="in_here" required="true" type="string">
<cfset isSOAP = isSOAPRequest()>
<cfif isSOAP>
<!--- Get the first header as a string and as XML. --->
<cfset username = getSOAPRequestHeader("http://mynamespace/", "username")>
<cfset return = "The service saw username: " & username>
<cfset xmlusername = getSOAPRequestHeader("http://mynamespace/", "username", "TRUE")>
<cfset return = return & "<br> as XML: " & xmlusername>
<!--- Get the second header as a string and as XML. --->
<cfset password = getSOAPRequestHeader("http://mynamespace/", "password")>
<cfset return = return & "The service saw password: " & password>
<cfset xmlpassword = getSOAPRequestHeader("http://mynamespace/", "password", "TRUE")>
<cfset return = return & "<br> as XML: " & xmlpassword>
<!--- Add a header as a string. --->
<cfset addSOAPResponseHeader("http://www.tomj.org/myns",
"returnheader", "AUTHORIZED VALUE", false)>
<!--- Add a second header using a CFML XML value. --->
<cfset doc = XmlNew()>
<cfset x = XmlElemNew(doc, "http://www.tomj.org/myns", "returnheader2")>
<cfset x.XmlText = "hey man, here I am in XML">
<cfsetx.XmlAttributes["xsi:type"] = "xsd:string">
<cfset tmp = addSOAPResponseHeader("ignoredNameSpace", "ignoredName", x)>
<cfelse>
<!--- Add a header as a string - Must generate error!
<cfset addSOAPResponseHeader("http://www.tomj.org/myns",
"returnheader", "AUTHORIZED VALUE", false)>
--->
<cfset return = "Not invoked as a web service">
</cfif>
<cfreturn return>
</cffunction>
</cfcomponent>
```
## Get help faster and easier
New user?
Quick links
