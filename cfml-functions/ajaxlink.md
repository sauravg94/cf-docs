# AjaxLink

### Description

Causes an HTML href attribute to display link results in the current Ajax container. When the browser follows a link that is specified by this function, the HTTP response does not replace the current page; instead, it populates the containing cfdiv, cflayoutarea, cfpod, or cfwindow control.
### Returns

Code that causes the linked page to be displayed in the containing control.
### Category

Display and formatting functions
### Function syntax

AjaxLink(URL)
### See also

cfdiv, cflayoutarea, cfpod, cfwindow, Using Ajax User Interface Components and Features in the Developing ColdFusion Applications
### History

### Parameters

Parameter
Description
URL
### Usage

This function has an effect only when it is used to specify the URL of an href attribute when the HTML a tag is inside a cfdiv, cflayoutarea, cfpod, or cfwindow control. Otherwise, the link has its normal effect.To prevent cross-site scripting, ColdFusion does not load a remote web page.
### Example

```coldfusion
<cfpod height="600" width="600" name="podTest">
<a href="<cfoutput>#AjaxLink('HelloWorld.cfm')#</cfoutput>">Click me</a>
</cfpod>
```
## Get help faster and easier
New user?
Quick links
