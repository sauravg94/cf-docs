---
description: Absolute function
---

# Abs

### Description

Absolute-value function. The absolute value of a number is the number without its sign.

### Returns

The absolute value of a number.

### Category

Mathematical functions

### Function syntax

Abs(number)

### See also

Sgn

### Parameters

Parameter Description number A number

### Example

```javascript
<h3>Abs Example</h3>
    <p>The absolute value of the following numbers:
1,3,-4,-3.2,6 is
<cfoutput>
#Abs(1)#,#Abs(3)#,#Abs(-4)#,#Abs(-3.2)#,#Abs(6)#
</cfoutput>
<p>The absolute value of a number is the number without its sign.</p>
<p> Output of the code in cfscript is </p>
<cfscript>
n1 = -5;
n2 = -(-6);
n3 = -(7);
writeOutput("the absolute of -5 is " );
writeOutput(Abs(n1));
writeoutput(" <br> ") ;
writeOutput("the absolute of -(-6) is  " );
writeOutput(Abs(n2));
writeoutput("<br>") ;
writeOutput("the absolute of (7) is " );
writeOutput(Abs(n3));
writeoutput("<br>") ;
</cfscript>
```

## Get help faster and easier

New user? Quick links
