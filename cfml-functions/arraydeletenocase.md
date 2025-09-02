# ArrayDeleteNoCase

### Description

Searches an array for the first position of a specified object and deletes it. The function searches for simple objects such as strings and numbers. Simple object string searches are case-insensitive. This function does not support searches for COM and CORBA objects.
### Returns

The updated array after deleting the specified element.
### Category

Array functions
### History

### Function syntax

```coldfusion
ArrayDeleteNoCase(array,value)
```
### See also

ArrayDeleteAt, ArrayClear
### Parameters

Parameter
Description
array
(Required) Array to search in.
value
### Example

```coldfusion
<cfscript>
myArray=ArrayNew(1);
myArray=["Analyze","Analyse","Analysis","analyse","analysis","analyze"];
WriteOutput(ArrayDeleteNoCase(myArray,"analyze")); // Returns true because object matches an element in the array
WriteOutput(SerializeJSON(myArray)); // Returns array after deleting the first element in the array
</cfscript>
```
### Output
["Analyse","Analysis","analyse","analysis","analyze"]
### Using member function
```coldfusion
<cfscript>
myArray=ArrayNew(1);
myArray=["Analyze","Analyse","Analysis","analyse","analysis","analyze"];
WriteDump(myArray.DeleteNoCase("analyze"));
</cfscript>
```
## Get help faster and easier
New user?
Quick links
