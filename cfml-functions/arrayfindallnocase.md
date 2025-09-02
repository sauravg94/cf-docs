# ArrayFindAllNoCase

### Description

Searches an array for all positions of a specified object. The function searches for simple objects such as strings and numbers or for complex objects such as structures. When the second parameter is a simple object, string searches are not case-sensitive. This function does not support searches for COM and CORBA objects.
Note that ArrayFindAllNoCase() behaves identically to ArrayFindAll(), except in the special cases where the second parameter is a function or you are searching for a string in an array of strings. When the second parameter is a function, ArrayFindAll() executes the function for each element in the array and ArrayFindAllNoCase() searches the array for the function.
### Returns

Array of indices in which the object was found.
### Category

Array functions
### History

- parallel
- maxThreadCount
### Syntax

```coldfusion
arrayFindAllNoCase(array, value or callback [, parallel] [, maxThreadCount])
```
### See also

Other array functions.
### Parameters

Parameter
Description
array
Array to search in.
value
Value to search for in the array.
callback
Inline function executed for each element in the array. Returns true if the array elements match the search criterion.
parallel
True if you want to enable parallel programming.
maxThreadCount
The number of threads the function can execute. The number of threads must be between 1-50. If the value exceeds 50, there is an exception.
### Example

```coldfusion
<cfscript>
writeDump(ArrayFindAllNoCase(["STRING","string"], "string"));
</cfscript>
```
### Using parallelization
```coldfusion
<cfscript>
for(i=1;i<=10000001;i++){
if(i == 554)
arr[i]= 'ABBBAB'
else if(i == 768)
arr[i]='KKKKKK'
else
arr[i] = 'abbaa';
}
writeoutput("<br>ArrayFindAllNoCase with parallel as false : ")
writeoutput(arrayfindallnocase(arr,'abbbab',false)[1])
writedump(arrayfindallnocase(arr,'ABBAA',true,5))
writeoutput("<br>ArrayFindAll with 5 parallel threads: ")
writeoutput(arr.findallnocase('abbbab',true,5)[1])
writeoutput("<br>ArrayFindAll with 40 parallel threads: ")
writeoutput(arrayfindallnocase(array=arr,value='abbbab',parallel=true,maxthreadcount=40)[1])
</cfscript>
```
## Get help faster and easier
New user?
Quick links
