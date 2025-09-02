# BinaryEncode

### Example 2

```coldfusion
<cfscript>
longString = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890`~!@##$%^&*()_+=-{}[]|\:;""'<>?,./";
binaryString = toBinary(toBase64(longString));
//encode binary data
encodedBinaryData = binaryEncode(binaryString, "Base64Url");
writedump(encodedBinaryData);
//decode the encoded binary data
decodedBinaryData = binaryDecode(encodedBinaryData, "Base64Url");
//verify if the decoded binary data is the same as the source binary data
writeOutput("<br/>")
if(toString(binaryString) eq toString(decodedBinaryData))
{
writeoutput("binaryEncode/binaryDecode of a long string is OK");
}
else
{
writeoutput("binaryEncode/binaryDecode of a long string is NOT OK");
}
</cfscript>
```
### Output
YWJjZGVmZ2hpamtsbW5vcHFyc3R1dnd4eXpBQkNERUZHSElKS0xNTk9QUVJTVFVWV1hZWjEyMzQ1Njc4OTBgfiFAIyQlXiYqKClfKz0te31bXXxcOjsiJzw-PywuLw binaryEncode/binaryDecode of a long string is OK
## Get help faster and easier
New user?
Quick links
