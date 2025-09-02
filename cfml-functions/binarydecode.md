# BinaryDecode

### Example

```coldfusion
<cfscript>
function base64ToHex( String base64Value ){
var binaryValue = binaryDecode( base64Value, "base64" );
var hexValue = binaryEncode( binaryValue, "hex" );
return( lcase( hexValue ) );
}
function base64ToString( String base64Value ){
var binaryValue = binaryDecode( base64Value, "base64" );
var stringValue = toString( binaryValue );
return( stringValue );
}
function hexToBase64( String hexValue ){
var binaryValue = binaryDecode( hexValue, "hex" );
var base64Value = binaryEncode( binaryValue, "base64" );
return( base64Value );
}
function hexToString( String hexValue ){
var binaryValue = binaryDecode( hexValue, "hex" );
var stringValue = toString( binaryValue );
return( stringValue );
}
function stringToBase64( String stringValue ){
var binaryValue = stringToBinary( stringValue );
var base64Value = binaryEncode( binaryValue, "base64" );
return( base64Value );
}
function stringToBinary( String stringValue ){
var base64Value = toBase64( stringValue );
var binaryValue = toBinary( base64Value );
return( binaryValue );
}
function stringToHex( String stringValue ){
var binaryValue = stringToBinary( stringValue );
var hexValue = binaryEncode( binaryValue, "hex" );
return( lcase( hexValue ) );
}
// ------------------------------------------------------ //
// ------------------------------------------------------ //
// ------------------------------------------------------ //
// ------------------------------------------------------ //
// Let's create a string value to test with.
message = "GoodMorning! What's Up?";
writeOutput( "Original :: " & message );
writeOutput( "<br />" );
// Now, let's check to the String-to-XXX conversions.
writeOutput( "<br />" );
messageAsHex = stringToHex( message );
writeOutput( "Hex :: " & messageAsHex );
writeOutput( "<br />" );
messageAsBase64 = stringToBase64( message );
writeOutput( "Base64 :: " & messageAsBase64 );
writeOutput( "<br />" );
messageAsBinary = stringToBinary( message );
writeOutput( "Binary :: B" & arrayLen( messageAsBinary ) );
writeOutput( "<br />" );
</cfscript>
```
Output:
Original :: GoodMorning! What's Up? Hex :: 476f6f644d6f726e696e6721205768617427732055703f Base64 :: R29vZE1vcm5pbmchIFdoYXQncyBVcD8= Binary :: B23
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
