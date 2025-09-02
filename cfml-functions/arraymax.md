# ArrayMax

### Example

```coldfusion
<cfscript>
myArray=[23,76,1,-43,9,112]
maxVal=ArrayMax(myArray)
WriteOutput(maxVal)// Returns 112
</cfscript>
```
### Using parallelization
```coldfusion
<cfscript>
for(i=1;i<=1001;i++){
arr[i] = i*2;
if(i == 554)
arr[i]= 2147483648
}
//writedump(arr)
//writeoutput(arr.max())
t_start=GetTickCount()
writeoutput(arraymax(arr,true,5))
t_end=GetTickCount()
writeoutput("<br>Time taken with 5 threads:" &  t_end-t_start)
t_start=GetTickCount()
writeoutput(arr.max(true,10))
t_end=GetTickCount()
writeoutput("<br>Time taken with 10 threads:" &  t_end-t_start)
t_start=GetTickCount()
writeoutput(arraymax(array=arr,parallel=true,maxthreadcount=20))
t_end=GetTickCount()
writeoutput("<br>Time taken with 20 threads:" &  t_end-t_start)
t_start=GetTickCount()
writeoutput(arr.max())
t_end=GetTickCount()
writeoutput("<br>Time taken with no parallel:" &  t_end-t_start)
</cfscript>
```
## Get help faster and easier
New user?
Quick links
