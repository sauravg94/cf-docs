# ArrayFilter

### Description

Used to filter the elements of an array.
### Returns

A new array
### Category

Array functions
### Syntax

```coldfusion
arrayFilter(array, function(item [,index, array]){} [, parallel] [, maxThreadCount])
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
Name of the array object.
filter
Inline function executed for each element in the array. Returns true if the array element has to be included in the resultant array. The callback function accepts these parameters:
- item
- index (optional)
- array (optional)
parallel
True if you want to enable parallel programming.
maxThreadCount
The number of threads the function can execute. The number of threads must be between 1-50. If the value exceeds 50, there is an exception.
For more information, check the blog by Jon Whish. John has detailed examples of using this function.
### Example

```coldfusion
<cfscript>
superheroes=[
{"name":"Iron Man","member":"Avengers"},
{"name":"Wonder Woman","member":"Justice League"},
{"name":"Hulk","member":"Avengers"},
{"name":"Thor","member":"Avengers"},
{"name":"Aquaman","member":"Justice League"}
];
avengers=ArrayFilter(superheroes,function(item){
return item.member=="Avengers";
});
writeDump(avengers);
</cfscript>
```
Output
Example with callback - Taken from John's blog.
```coldfusion
<cfscript>
a = [1,2,3,4,5,6,7,8,9,10];
result = ArrayFilter(a,function(el, index) {
return index % 2;
});
writeDump(result); // [1,3,5,7,9]
</cfscript>
```
### Using parallelization
```coldfusion
<cfscript>
for(i=1;i<=1001;i++){
arr[i] = RepeatString("LoremIpsum",i)
if (i == 264)
arr[i] = 'wwwwxxxx'
}
function callback(item,index){
if (item.contains("wwww"))
return true
return false
}
writeoutput("<br>ArrayFilter with parallel set to false: " )
writeoutput(arr.filter(callback,false)[1])
writeoutput("<br>ArrayFilter with 5 parallel threads: ")
writeoutput(arrayfilter(arr,callback,true,5)[1])
try{
writeoutput("<br>Time taken with negative maxthreadcount :")
writedump(arr.filter(callback,true,-10))
}
catch(any e){
writeoutput("Type: " & e.type & " Message:" &  e.message  )
}
try{
writeoutput("<br>Time taken with more than 50 threads :")
writeoutput(arr.filter(callback,true,150)[1])
}
catch(any e){
writeoutput("Type: " & e.type & " Message:" &  e.message  )
}
writeoutput("<br>ArrayEvery with parallel set as true and with no threads specified, will take thread count from cf admin: ")
writeoutput(arrayfilter(array=arr,callback=callback,parallel=true)[1])
</cfscript>
```
## Get help faster and easier
New user?
Quick links
