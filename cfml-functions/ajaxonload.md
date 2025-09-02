# AjaxOnLoad

### Description

Causes the specified JavaScript function to run when the page loads.
### Returns

This function does not return a value.
### Category

Display and formatting functions
### Function syntax

AjaxOnLoad(functionName)
### See also

cfdiv, cflayoutarea, cfpod, cfwindow, Using Ajax User Interface Components and Features in the Developing ColdFusion Applications
### History

### Parameters

Parameter
Description
functionName
The name of the function to run when the page loads. The specified function does not take a parameter.
### Usage

This function causes a JavaScript function to run when a page loads in the browser. The JavaScript function can perform any initialization actions that are required for the page to function properly. For example, a login window might open on a page if the user is not already logged in. You can use the AjaxOnLoad function to specify a JavaScript function that determines the login status and opens the window only if needed.You can use this function on top-level pages, or on pages that you dynamically include in your application by using the source attribute of the cfpod and cfwindow tags.
### Example

The following example uses the AjaxOnLoad function to call an init function each time the page loads. The init function displays a login window.
```coldfusion
<html>
<head>
<title>Enter Mail Login Details</title>
<script>
init = function() {
}
</script>
</head>
<body>
<cfwindow name="loginwindow" title="Enter Login Details"
draggable="false" closable="false" resizable="false"
width="450" height="200">
<cfoutput>
<form action="#cgi.script_name#" method="post" name="loginform">
<table width="400" class="loginTable" cellpadding="5">
<tr>
<td style="text-align: right">mail server:</td>
<td><input type="text" name="server"></td>
</tr>
<tr>
<td style="text-align: right">username:</td>
<td><input type="text" name="username"></td>
</tr>
<tr>
<td style="text-align: right">password:</td>
<td><input type="password" name="password"></td>
</tr>
<tr>
<td>&nbsp;</td>
<td><input type="submit" name="login" value="Login"></td>
</tr>
</table>
</form>
</cfoutput>
</cfwindow>
<cfset AjaxOnLoad("init")>
</body>
</html>
```
## Get help faster and easier
New user?
Quick links
