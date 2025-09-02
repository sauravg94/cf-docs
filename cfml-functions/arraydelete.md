# ArrayDelete

### Description

Searches an array for the first position of a specified object and deletes it. The function searches for simple objects such as strings and numbers or for complex objects such as structures. Simple object string searches are case-sensitive. This function does not support searches for COM and CORBA objects.
### Returns

The updated array.
### Category

Array functions
### Function syntax

ArrayDelete(array,value)
### History

- Introduced named parameters.
- Returns the updated array.
### See also

#### ArrayDeleteAt, ArrayClear
### Parameters

Parameter
Description
array
Array to search in.
value
Value to search for.
### Example

```coldfusion
<cfscript>
myArray=["London", "New York", "Paris", "Barcelona", "Berlin", "Tokyo", "Seattle"];
WriteOutput("Input array is: ");
writeDump(myArray)
// Delete "Paris"
ArrayDelete(myArray,"Paris"); // Returns True since Paris is a member of myArray
WriteOutput("Array after deleting Paris is: ");
writeDump(myArray)
</cfscript>
```
### Output
## Get help faster and easier
New user?
Quick links
