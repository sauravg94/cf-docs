# ArrayEach

### Description

Loops over an array.
### Returns

Nothing
### Category

Array functions
### Syntax

arrayEach(array, function(item, [index, [array]]){} [, parallel] [, maxThreadCount])
### See also

Other array functions
### History

- parallel
- maxThreadCount
### Parameters

Parameter
Description
array
Name of the array.
callback
Closure function executed for each element in the array.
parallel
True if you want to enable parallel programming.
maxThreadCount
The number of threads the function can execute. The number of threads must be between 1-50. If the value exceeds 50, there is an exception.
### Basic example using the callback function
```coldfusion
<cfscript>
myCities=["London","New York","Paris","Tokyo","Barcelona"];
// Create a function that takes city as an argument  and prints the name of the cities as output
// with delimiter as space
ArrayEach(myCities,function(city){
WriteOutput(city & "  ");
}
);
</cfscript>
```
### Output
London New York Paris Tokyo Barcelona
### Passing array index to callback functions in ArrayEach
```coldfusion
<cfscript>
cityArray = ["San Jose","New york","Boston", "Las Vegas"];
function printArrayCity(city, index)
{
writeOutput("<br>" & city & "   is at index " &  index);
}
ArrayEach(cityArray ,printArrayCity);
</cfscript>
```
### Output
San Jose is at index 1New york is at index 2Boston is at index 3Las Vegas is at index 4
### Passing array to the closure function
Also, the original array can also be passed to the closure function. So the following code is also valid:
```coldfusion
function printArrayCity(city, index, cityArray)
{
}
...
```
For example,
```coldfusion
<cfapplication passarraybyreference="true">
<cfscript>
cityArray=["London","New York","Paris","Tokyo","Barcelona"];
function printArray(city,index,cityArray)
{
cityArray[index] = city & " is visited.";
}
WriteOutput("The original array is:");
WriteDump(cityArray);
ArrayEach(cityArray,printArray);
WriteOutput("The new array is:");
WriteDump(cityArray);
</cfscript>
```
### Output
### Using parallelization
```coldfusion
<cfscript>
for(i=1;i<=1001;i++){
arr[i] = RepeatString("LoremIpsum",i)
if (i == 264)
arr[i] = 'wwwwxxxx'
}
function callback(item,index){
item = item & "ss";
if (index == 264)
writeoutput(item & "<br>");
return item;
}
writeoutput("output after no parallel for arr[264]:")
arr.each(callback,false)
writeoutput("output  with 5  parallel threads for arr[264]:")
arrayeach(arr,callback,true,5)
writeoutput("output  with 10  parallel threads for arr[264]:" )
arr.each(callback,true,10)
writeoutput("output  with 20 parallel threads for arr[264]:" )
arrayeach(array=arr,callback=callback,parallel=true,maxthreadcount=20)
writeoutput("output  with 40  parallel threads for arr[264]:" )
arrayeach(array=arr,callback=callback,parallel=true,maxthreadcount=40)
writeoutput("output  with   parallel threads taken from server for arr[264]:" )
arrayeach(array=arr,callback=callback,parallel=true)
try{
writeoutput("with negative thread ,should throw exception:" & "<br>")
arr.each(callback,true,-5)
}
catch(any e){
writeoutput("Type: " & e.type & " Message:" &  e.message  )
}
try{
writeoutput("<br>with more than 50 thread ,should throw exception:" & "<br>")
arr.each(callback,true,105)
}
catch(any e){
writeoutput("Type: " & e.type & " Message:" &  e.message  )
}
</cfscript>
```
## Get help faster and easier
New user?
Quick links
