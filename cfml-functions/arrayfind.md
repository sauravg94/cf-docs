# ArrayFind

### Description

Searches an array for the first position of a specified object. The function searches for simple objects such as strings and numbers or for complex objects such as structures. When the second parameter is a simple object, string searches are case-sensitive. This function does not support searches for COM and CORBA objects.
### Returns

Index in the array of the first match, or 0 if there is no match.
### Category

Array functions
### History

### Syntax

```coldfusion
arrayFind(array, value)
```
### See also

ArrayFindNoCase
### Parameters

Parameter
Description
array
Array to search in.
callback
Inline function executed for each element in the array. Returns true if the array element matches the search criterion.
value
Value to search for in the array.
### Example

```coldfusion
<cfscript>
writeDump(ArrayFind(["STRING","string"], "string"));
writeDump(ArrayFind(["STRING","string"], function(s) {if(compare(s, "string")==0) return true; return false;}));
</cfscript>
```
## Get help faster and easier
New user?
Quick links
