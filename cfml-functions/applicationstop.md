# ApplicationStop

### Description

Stops or resets the current application. The application is restarted on the next request to the application.
### Returns

void
### Category

Other functions
### Function syntax

applicationstop()
### History

Added in ColdFusion 9.
### Example

```coldfusion
<!---- get artist by id ---->
<cftry>
...
....
<!---stops the application to reset the artistid, if the artworks for the artist do not exist--->
<cfset applicationstop()/>
<cfset artist = EntityLoad( "artist", url.artistid, True ) />
<cfoutput>
<h2>#artist.getFullName()#</h2>
<table width="400">
<tr>
<th>Item</th>
<th>Price</th>
<th>Sold</th>
</tr>
<cfloop array="#artist.getArt()#" index="index">
<tr>
<td>#index.getArtName()#</td>
<td>#index.getPrice()#</td>
<td>#index.getIsSold()#</td>
</tr>
</cfloop>
</table>
<p><a href="index.cfm">View list</a></p>
</cfoutput>
<cfcatch type = "any">
<cfoutput>Artworks for the selected artists are not available</cfoutput>
</cfcatch>
</cftry>
```
## Get help faster and easier
New user?
Quick links
