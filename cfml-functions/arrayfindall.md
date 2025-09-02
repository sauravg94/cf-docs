# ArrayFindAll

### Description

Searches an array for all positions of a specified object. The function searches for simple objects such as strings and numbers or for complex objects such as structures. When the second parameter is a simple object, string searches are case-sensitive. This function does not support searches for COM and CORBA objects.
### Returns

Array of indices in which the object was found.
### History

- parallel
- maxThreadCount
### Category

Array functions
### Syntax

```coldfusion
arrayFindAll(array, value or callback [, parallel] [, maxThreadCount])
```
### See also

Other array functions.
### History

- parallel
- maxThreadCount
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
writeDump(ArrayFindAll(["STRING","string"], "string"));
writeDump(ArrayFindAll(["STRING","string"], function(s) {if(compare(s, "string")==0) return true; return false;}));
</cfscript>
```
### Using parallelization
```coldfusion
<cfscript>
for(i=1;i<=100001;i++){
if(i == 554)
arr[i]= -2147483648
else if(i == 768)
arr[i]=200
else
arr[i] = i*2;
}
writeoutput("<br>ArrayFindAll with parallel set to false: ")
writeoutput(arrayfindall(arr,200,false)[1])
writeoutput("<br>ArrayFindAll with 5 parallel threads: ")
writeoutput(arrayfindall(arr,200,true,5)[1])
writeoutput("<br>ArrayFindAll with negative number of  threads: ")
try{
arr.findall(200,true,-10)
}
catch(any e){
writeoutput("Type: " & e.type & " Message:" &  e.message  )
}
writeoutput("<br>ArrayFindAll with 20 parallel threads: ")
writeoutput(arrayfindall(array=arr,value=200,parallel=true,maxthreadcount=20)[1])
writeoutput("<br>ArrayFindAll with more than 50 parallel threads: ")
try{
arr.findall(200,true,100)
}
catch(any e){
writeoutput("Type: " & e.type & " Message:" &  e.message  )
}
writeoutput("<br>ArrayFindAll with parallel and with no threads specified, will take thread count from cf admin:  ")
writeoutput(arr.findall(200,true)[1])
</cfscript>
```
## Get help faster and easier
New user?
Quick links
