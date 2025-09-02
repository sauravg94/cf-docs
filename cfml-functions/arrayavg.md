# ArrayAvg

### Description

Calculates the average of the values in an array.
### Returns

Number. If the array parameter value is an empty array, returns zero.
### Category

Array functions, Mathematical functions
### Function syntax

arrayAvg(array [, parallel] [, maxThreadCount])
### History

- parallel
- maxThreadCount
### See also

ArraySum; Basic array techniques in the Developing ColdFusion Applications
### Parameters

Parameter
Description
array
(Required) The array containing the values.
parallel
(Optional) True if you want to enable parallel programming.
maxThreadCount
(Optional) The number of threads the function can execute. The number of threads must be between 1-50. If the value exceeds 50, there is an exception.
### Usage

The following example uses the ArrayAvg function to get the average value of an array.
### Example

```coldfusion
<cfscript>
myArray=[1,2,3,4,5,5.5,6,7,8,9];
writeOutput(ArrayAvg(myArray)); // returns 5.05
</cfscript>
```
### Output
5.05
### Using parallelization
```coldfusion
<cfscript>
for(i=1;i<=1001;i++){
arr[i] = i/2;
if (i === 1000)
arr[i] = i;
}
function callback(item,index){
item = item + 2;
return item;
}
writeoutput("with third param as false , i.e no parallel:" & arr.map(callback).avg(false,2) & "<br>")
try{
writeoutput("with negative thread ,should throw exception:" & "<br>")
arr.map(callback).avg(true,-5)
}
catch(any e){
writedump("Type: " & e.type & " Message:" &  e.message  )
}
writeoutput("<br>with 10 threads :" & arr.map(callback).avg(true,10) & "<br>")
arr =arraymap(array=arr,callback=callback)
writeoutput("with 20 threads : " & arrayavg(array=arr,parallel=true,maxthreadcount=20) & "<br>")
arr=arraymap(array=arr,callback=callback)
writeoutput("with 50 threads :" & arrayavg(array=arr,parallel=true,maxthreadcount=50) & "<br>")
try{
writeoutput("with more than 50  thread ,should throw exception" & "<br>")
arr.map(callback).avg(true,100);
}
catch(any e){
writedump("Type: " & e.type & " Message:" &  e.message )
}
arr =arraymap(array=arr,callback=callback)
writeoutput("<br> with no threads specified, will take thread count from cf admin: " & arrayavg(array=arr,parallel=true) & "<br>")
</cfscript>
```
## Get help faster and easier
New user?
Quick links
