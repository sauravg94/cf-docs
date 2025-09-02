# ArrayInsertAt

### Description

Inserts a value into an array. Array elements whose indexes are equal to or greater than the new position are incremented by one. The array length increases by one.
### Returns

Returns the updated array with the specified element inserted.
### Category

Array functions
### Function syntax

ArrayInsertAt(array, position, value)
### See also

ArrayDeleteAt; Functions for XML object management in Modifying a ColdFusion XML object in the Developing ColdFusion Applications
### History

- Changed behavior: This function can be used on XML objects.
- Changed thrown exceptions: This function can throw the InvalidArrayIndexException error.
### Parameters

Parameter
Description
array
Name of an array
position
Index position at which to insert value
value
Value to insert
### Usage

To apply the ArrayInsertAt() function to a multidimensional array, you must specify all but the last index in the array parameter. The following example inserts an element at myarray24:
<cfset ArrayInsertAt(myarray[2], 4, "test")>
### Throws
If this function attempts to insert an element at position 0, or specifies a value for position that is greater than the size of array, this function throws an InvalidArrayIndexException error.
### Example

```coldfusion
<cfscript>
myCities=["London","New York","Paris","Tokyo","Barcelona"];
WriteOutput("The input array is: ");
WriteOutput(serializeJSON(myCities) & "|");
// Insert the city "Berlin" in myCities after "Paris" at index four
ArrayInsertAt(myCities,4,"Berlin"); // Returns True
WriteOutput("Array after inserting Berlin is: ");
WriteOutput(serializeJSON(myCities)); // returns output array with Berlin as new element
</cfscript>
```
### Output
The input array is: ["London","New York","Paris","Tokyo","Barcelona"]|Array after inserting Berlin is: ["London","New York","Paris","Berlin","Tokyo","Barcelona"]
### Example- Insert a value in an empty array

```coldfusion
<cfscript>
a = [] // empty array
arrayInsertAt(a, 1, "Value");
writeDump(a);
</cfscript>
```
The value is inserted into position one in the array.
### Example 2- Non-empty array

```coldfusion
<cfscript>
a = []; // empty array
a[1] = "Value1"; // add first element
arrayInsertAt(a, 2, "Value2"); // add second element
writeDump(a)
</cfscript>
```
## Get help faster and easier
New user?
Quick links
