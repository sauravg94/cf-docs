# ArrayContains

### Description

Searches an array for the presence of a specified object. The function searches for simple objects such as strings and numbers or for complex objects such as structures. Simple object string searches are case-sensitive. This function does not support searches for COM and CORBA objects.
### Returns

Yes, if the specified object exists in the array.
### History

### Category

Array functions
### Function syntax

ArrayContains(array,value)
### See also

ArrayFind, ArrayFindNoCase
### Parameters

Parameter
Description
array
Array to search in.
value
Object to search for.
### Example

```coldfusion
<cfscript>
myArray=[1,2,3,4,5];
writeoutput(ArrayContains(myArray,3) & " | "); //returns True since 3 is a member of myArray
writeoutput(ArrayContains(myArray,6)); //returns False since 6 is not a member of myArray
</cfscript>
```
### Output
YES | NO
## Get help faster and easier
New user?
Quick links
