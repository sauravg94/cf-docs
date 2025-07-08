# cflogout

Logs the current user out. Removes knowledge of the user ID, password, and roles from the server. If you do not use this tag, the user is automatically logged out when the session ends.

## Category
Security tags

## Usage

cfml
<cflogout session="all|current|others" applicationToken="token">


## Attributes

| Attribute | Description | Default |
|-----------|-------------|---------|
| session | When invoked, which session should be logged out. This is a string. The possible values are: all, current, others | current |
| applicationToken | When using application token attribute for cflogin, the cookie that gets created uses the application token CFAUTHORIZATION_applicationtoken. The applicationtoken attribute has been added for cflogout tag so that the same application token can be specified here in the cflogout tag | Application Name |

## See also
- cflogin
- cfloginuser
- GetAuthUser
- GetUserRoles
- IsUserInAnyRole
- IsUserInRole
- IsUserLoggedIn
- Securing Applications in Developing ColdFusion Applications

## History
- ColdFusion 2016 release Update 4: Added the applicationToken attribute
- ColdFusion 11 Update 12: Added the applicationToken attribute
- ColdFusion 11: Added the session attribute
- ColdFusion MX 6.1: Changed behavior: if the Session scope is enabled, a login remains in effect until the session expires or the user is logged out by the cflogout tag
- ColdFusion MX: Added this tag

## Example

```
<cflogin>
    <cfloginuser name = "foo" password="bar" roles = "admin">
</cflogin>

<cfoutput>Authorized user: #getAuthUser()#</cfoutput>

<cflogout>

<cfoutput>Authorized user: #getAuthUser()#</cfoutput>
```


```
<cflogin>
    <cfloginuser name = "foo" password="bar" roles = "admin">
</cflogin>

<cfoutput>Authorized user: #getAuthUser()#</cfoutput>

<cflogout>

<cfoutput>Authorized user: #getAuthUser()#</cfoutput>
```


```
<cflogin>
    <cfloginuser name = "foo" password="bar" roles = "admin">
</cflogin>

<cfoutput>Authorized user: #getAuthUser()#</cfoutput>

<cflogout>

<cfoutput>Authorized user: #getAuthUser()#</cfoutput>
```
