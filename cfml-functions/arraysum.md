# ArraySum

### Example

```coldfusion
<cfscript>
myArray=[921,22,133,40,345,58,-6];
WriteOutput("Sum of values in myArray is:");
WriteOutput(ArraySum(myArray) & "|"); // returns sum of values in myArray
myNewArray=[];
WriteOutput("Sum of values in myNewArray is:");
WriteOutput(ArraySum(myNewArray)); //returns zero since myNewArray is empty
</cfscript>
```
Output
Sum of values in myArray is:1513|Sum of values in myNewArray is:0
### Example - using the ignoreEmpty parameter

```coldfusion
<cfscript>
myarray=ArrayNew(1);
myarray=[-23,56,97,javacast("null",""),"",1,23];
sum=arraysum(myarray,true); //ignoreEmpty=true
writeoutput(sum);
</cfscript>
```
### Output
154
### Using parallelization
```coldfusion
<cfscript>
for(i=1;i<=100000;i++){
if(i === 4500)
arr[i]=0;
else
arr[i]=i*2;
}
sum= arr.map(function(item){
return item/2;
},true,20).sum(false,true,10)
writeoutput(sum & "<br>");
sum = arraysum(array=arr,ignoreempty=true,parallel=true,maxthreadcount=10)
writeoutput(sum & "<br>");
sum1 = arraysum(arr,false,true,10)
writeoutput(sum1 & "<br>");
</cfscript>
```
## Get help faster and easier
New user?
Quick links
