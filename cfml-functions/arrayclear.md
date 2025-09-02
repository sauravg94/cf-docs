# ArrayClear

### Description

Deletes the data in an array.
### Returns

An empty array.
### Syntax

```coldfusion
ArrayClear(array)
```
### Parameters

Parameter
Description
array
Name of an array
### History

### Category

Array functions
### See also

- ArrayDeleteAt
- Functions for XML object management in Modifying a ColdFusion XML object in the Developing ColdFusion Applications
### Example

```coldfusion
<cfscript>
myArray=[1,2,3,4,5];
// Clear myArray
WriteOutput(ArrayClear(myArray)); // Clears the array and returns True
WriteDump(myArray); // Returns an empty array
</cfscript>
```
### Output
YES
## Get help faster and easier
New user?
Quick links
