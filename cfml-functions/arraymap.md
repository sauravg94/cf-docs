# ArrayMap

### See also

ArrayFilter, ArrayReduce
### Example

```coldfusion
<cfscript>
myArray=ArrayNew(1);
myArray = [ 1,5,7,9,11 ];
newArray = arrayMap(myArray, function(item){
return item;
});
writeDump(newArray);
</cfscript>
```
### Using parallelization
```coldfusion
<cfscript>
for(i=1;i<=100001;i++){
arr[i]=i
}
//writeDump(arr)
callback=function(item){
return sqr(item)
}
// without parallelization
t_start=GetTickCount()
newArray=arrayMap(arr,callback)
t_end=GetTickCount()
writeOutput("Time taken without parallelization: " & t_end-t_start)
writeOutput("<br/>")
// with parallelization
t_start=GetTickCount()
pArray=arrayMap(arr,callback,true,10)
t_end=GetTickCount()
writeOutput("Time taken with 10 threads: " & t_end-t_start)
writeOutput("<br/>")
// with parallelization
t_start=GetTickCount()
pArray=arrayMap(arr,callback,true,20)
t_end=GetTickCount()
writeOutput("Time taken with 20 threads: " & t_end-t_start)
writeOutput("<br/>")
// with parallelization
t_start=GetTickCount()
pArray=arrayMap(arr,callback,true,30)
t_end=GetTickCount()
writeOutput("Time taken with 30 threads: " & t_end-t_start)
writeOutput("<br/>")
// with parallelization
t_start=GetTickCount()
pArray=arrayMap(arr,callback,true,40)
t_end=GetTickCount()
writeOutput("Time taken with 40 threads: " & t_end-t_start)
writeOutput("<br/>")
</cfscript>
```
## Get help faster and easier
New user?
Quick links
