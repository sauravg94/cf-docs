# ArrayDeleteAt

### Description

Deletes an element from a specified position in an array. When an element is deleted, ColdFusion recalculates index positions. For example, in an array that contains the months of the year, deleting the element at position 5 removes the entry for May. After this, to delete the entry for June, you would delete the element at position 5 (not 6).
### Returns

A boolean value indicating if the array element has been successfully deleted.
### Category

Array functions
### Function syntax

ArrayDeleteAt(array, position)
### See also

ArrayInsertAt; Functions for XML object management in Modifying a ColdFusion XML object in the Developing ColdFusion Applications
### History

- Changed behavior: This function can be used on XML objects.
- Changed thrown exceptions: This function can throw the InvalidArrayIndexException error.
### Parameters

Parameter
Description
array
Name of an array.
position
### Throws
If this function attempts to delete an element at position 0, or specifies a value for position that is greater than the size of array, this function throws an InvalidArrayIndexException error.
### Example

```coldfusion
<cfscript>
myArray=["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"]
deleted=ArrayDeleteAt(myArray,2)
writeOutput(deleted)
</cfscript>
```
### Output
YES
## Get help faster and easier
New user?
Quick links
