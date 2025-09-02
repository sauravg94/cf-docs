# ArraySetMetaData

### Description

Sets metadata on the array element(s).
### Returns

Nothing
### History

Added in ColdFusion (2016 release) Update 2
### Category

Array functions
### See also

ArrayGetMetaData
### Syntax

```coldfusion
ArraySetMetaData(Array array, Struct metadata)
```
### Parameters

Parameter
Description
array
The input array.
metadata
The metadata to be applied to the array element(s).
### Example

```coldfusion
<cfscript>
inputs = ["2500.12", 4.0, "Yes", "False", "339090", {"q1": "Yes"}, ["1","yes","3","no","null","null"]];
metadata={items: ["numeric", "integer", "string", "boolean", "string", {q1: {type:"string",ignore:true}},
{items: ["integer","boolean","string","string","string","null"]}]};
ArraySetMetaData(inputs,metadata);
writeoutput(serializeJSON(inputs));
</cfscript>
```
### Output
[2500.12,4,"Yes",false,"339090",{},[1,true,"3","no","null","null"]]
## Get help faster and easier
New user?
Quick links
