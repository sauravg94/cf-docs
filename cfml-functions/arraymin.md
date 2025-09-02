# ArrayMin

### Example

```coldfusion
<cfscript>
myArray=[23,76,1,-43,9,112]
minVal=ArrayMin(myArray)
WriteOutput(minVal)// Returns -43
</cfscript>
```
### Using parallelization
```coldfusion
<cfscript>
for(i=1;i<=1001;i++){
arr[i] = i*2;
if(i == 554)
arr[i]= -2147483648
}
//writedump(arr)
//writeoutput(arr.min())
t_start=GetTickCount()
writeoutput(arraymin(arr,true,5))
t_end=GetTickCount()
writeoutput("<br>Time taken with 5 threads:" &  t_end-t_start)
t_start=GetTickCount()
writeoutput(arr.min(true,10))
t_end=GetTickCount()
writeoutput("<br>Time taken with 10 threads:" &  t_end-t_start)
t_start=GetTickCount()
writeoutput(arraymin(array=arr,parallel=true,maxthreadcount=20))
t_end=GetTickCount()
writeoutput("<br>Time taken with 20 threads:" &  t_end-t_start)
t_start=GetTickCount()
writeoutput(arr.min())
t_end=GetTickCount()
writeoutput("<br>Time taken with no parallel:" &  t_end-t_start)
</cfscript>
```
## Get help faster and easier
New user?
Quick links
