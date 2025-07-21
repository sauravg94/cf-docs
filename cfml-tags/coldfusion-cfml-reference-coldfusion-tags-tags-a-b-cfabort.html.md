## cfabort

#### Description

Stops the processing of a ColdFusion page at the tag location. ColdFusion returns everything that was processed before the tag. The tag is often used with conditional logic to stop processing a page when a condition occurs.

#### Category

[Flow-control tags](/coldfusion/cfml-reference/coldfusion-tags/tags-by-function/flow-control-tags.html)

#### Syntax

```
<cfabort 
showError = "error message">
```

|  |
| --- |
| ***Note:*** You can specify this tag's attributes in an attributeCollection whose value is a structure. Specify the structure name in the attributeCollection and use the tag's attribute names as structure keys. |

#### See also

[cfbreak](/coldfusion/cfml-reference/coldfusion-tags/tags-a-b/cfbreak.html) ,  [cfexecute](/coldfusion/cfml-reference/coldfusion-tags/tags-d-e/cfexecute.html) ,  [cfexit](/coldfusion/cfml-reference/coldfusion-tags/tags-d-e/cfexit.html) ,  [cfif](/coldfusion/cfml-reference/coldfusion-tags/tags-i/cfif.html) ,  [cflocation](/coldfusion/cfml-reference/coldfusion-tags/tags-j-l/cflocation.html) ,  [cfloop](/coldfusion/cfml-reference/coldfusion-tags/tags-j-l/cfloop.html) ,  [cfswitch](/coldfusion/cfml-reference/coldfusion-tags/tags-r-s/cfswitch.html) ,  [cfthrow](/coldfusion/cfml-reference/coldfusion-tags/tags-t/cfthrow.html) ,  [cftry](/coldfusion/cfml-reference/coldfusion-tags/tags-t/cftry.html) ;  [cfabort](/coldfusion/cfml-reference/coldfusion-tags/tags-a-b/cfabort.html)  and  [cfexit](/coldfusion/cfml-reference/coldfusion-tags/tags-d-e/cfexit.html)  in the *Developing ColdFusion Applications*

#### Attributes

| Attribute | Req/Opt | Default | Description |
| --- | --- | --- | --- |
| showError | Optional |  | Error to display, in a standard ColdFusion error page, when tag executes. |

#### Usage

When you use the  cfabort  and  cferror  tags together, the  cfabort  tag halts processing immediately; the  cferror  tag redirects output to a specified page. If this tag does not contain a showError attribute value, processing stops when the tag is reached and ColdFusion returns the page contents up to the line that contains the  cfabort  tag.  
When you use this tag with the showError attribute, but do not define an error page using  cferror , page processing stops when the  cfabort  tag is reached. The message in showError displays to the client .When you use this tag with the showError attribute and an error page using  cferror , ColdFusion redirects output to the error page specified in the  cferror  tag.

|  |
| --- |
| ***Note:*** When using cfabort , cflocation , or cfcontent tags, the OnAbort method is invoked instead on OnRequestEnd. |

#### Example

This example shows the use of  cfabort  to stop processing.

[![](/content/dam/help/en/coldfusion/cfml-reference/coldfusion-tags/tags-d-e/cfdocument/jcr_content/main-pars/image/CFFiddle.png)](https://cffiddle.org/app/file?filepath=d237e26c-4a69-459f-bc1e-c81251f8f36f/7cd2458c-3c6e-4992-aa28-48e9860fe22d/07dc77cd-c644-450f-b18c-25f127113f59.cfm)

```
<cftry>
 <!--- make a call to a non-existent function --->
 <cfset firstName = getFirstName(userId=10)>
<!--- catch any errors --->
<cfcatch type="any">
 <!--- dump the error to the browser --->
 <cfdump var="#cfcatch#">
 <!--- abort further processing --->
 <cfabort>
</cfcatch>
</cftry>
```

