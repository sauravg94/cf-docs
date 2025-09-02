# Asc

### Example

```coldfusion
<cfscript>
WriteOutput(Asc("") & "|"); //returns 0 since ASCII value of empty string is 0
WriteOutput(Asc("a") & "|"); //returns 97 since ASCII value of "a" is 97
WriteOutput(Asc("A") & "|"); //returns 65 since ASCIII value of "A" is 65
WriteOutput(Asc("null") & "|"); //returns 110 since ASCII value of "n" is 110
WriteOutput(Asc("Null")); //returns 78 since ASCII value of "N" is 78
</cfscript>
```
Output
0|97|65|110|78
## Get help faster and easier
New user?
Quick links
