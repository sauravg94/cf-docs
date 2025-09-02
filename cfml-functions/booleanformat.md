# BooleanFormat

### Description

This function takes a value and returns "true" or "false" depending on the value.
### Returns

"true", for a non-zero value; "false" for zero, false, and an empty string ("").
BooleanFormat(25) returns true. BooleanFormat(false) returns false.
The function throws an exception when you pass any string other than empty string ("").
For example, BooleanFormat("Hello") throws an exception.
But, BooleanFormat("true") or BooleanFormat("yes") returns true.
Similarly, BooleanFormat("false") or BooleanFormat("no") returns false.
Null value
- BooleanFormat("null"): Throws an exception because null is treated as a string.
- BooleanFormat(null): Null is treated as a variable, so will search for the value. If no such variable exists, an exception is thrown.
- BooleanFormat(javacast("null","null")): Here actual null is being passed, and hence it will return false.
### Category

Display and formatting functions
History
New in Adobe ColdFusion (2016 release)
### Syntax

```coldfusion
BooleanFormat(value)
```
### Parameters

Parameter
Description
value
A number, boolean value, null, or an empty string.
### Example

```coldfusion
<cfscript>
val=0;
str="1123";
writeoutput(BooleanFormat(val)); // returns false
writeoutput(BooleanFormat(str)); // returns true
</cfscript>
```
### Using member function
```coldfusion
<cfscript>
val=false;
WriteOutput(val.BooleanFormat());
</cfscript>
```
## Get help faster and easier
New user?
Quick links
