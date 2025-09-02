# ArrayFindNoCase

### Description

Searches an array for the first position of a specified object. The function searches for simple objects such as strings and numbers or for complex objects such as structures. When the second parameter is a simple object, string searches are not case-sensitive. This function does not support searches for COM and CORBA objects.
Note that ArrayFindNoCase() behaves identically to ArrayFind(), except in the special cases where the second parameter is a function or you are searching for a string in an array of strings. When the second parameter is a function, ArrayFind() executes the function for each element in the array and ArrayFindNoCase() searches the array for the function.
### Returns

Index in the array of the first match, or 0 if there is no match.
### Category

Array functions
### History

### Function syntax

```coldfusion
arrayFindNoCase(array, value [, parallel] [, maxThreadCount])
```
```coldfusion
ArrayFindNoCase(array, callback)
```
### See also

ArrayFind
### Parameters

Parameter
Description
array
Array to search in. Valid datatypes in array are:
- String
- Boolean
- Number
value
Value to search for in the array.
callback
Inline function executed for each element in the array. Returns true if the array element matches the search criterion.
parallel
True if you want to enable parallel programming.
maxThreadCount
The number of threads the function can execute. The number of threads must be between 1-50. If the value exceeds 50, there is an exception.
### Example

```coldfusion
<cfscript>
writeDump(ArrayFindNoCase(["STRING","string"], "string"));
writeDump(ArrayFindNoCase(["STRING","string"], function(s) {
if(compare(s, "string")==0)
return true;
else
return false;
}
));
</cfscript>
```
## Get help faster and easier
New user?
Quick links
