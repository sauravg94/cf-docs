# Security enhancements in ColdFusion 2016 release

> **Note:** The Security Code Analyzer is only available to ColdFusion 2016 release Enterprise license users.

For any web application, security plays a critical role. It is important to avoid security pitfalls while developing web applications.

## Security code analyzer

Security Analyzer is a new feature in Adobe ColdFusion 2016 release. This feature is integrated into ColdFusion Builder to enable developers to avoid common security pitfalls and vulnerabilities while writing ColdFusion code.

Use this feature to view:

- Vulnerable code in the editor
- Vulnerability or type of attack
- Error and Warning
- Severity level of vulnerability (High, Medium, and Low)
- Suggestion to avoid the vulnerability

> **Note:** Security Analyzer works only with ColdFusion Enterprise or Enterprise trial and with Developer profile. Security Analyzer does not work with ColdFusion Developer or Standard edition and with Production or Production secure profile. Security Analyzer does not work with ColdFusion Builder default local server.

The Security Analyzer feature of the server is exposed as a service, a request to which is made by the builder. You can get a list of security vulnerabilities for a file, folder, or a project.

## Accessing security analyzer in builder

Follow the steps below to access Security Analyzer in ColdFusion Builder:

1. Right-click the project folder or project file in the navigator pane
2. Choose Security Analyzer > Run Security Analyzer

![Security Analyzer](Security-Analyzer.png)

You have three options in Security Analyzer:

- **Run Security Analyzer** - Analyzes and displays vulnerabilities of the code
- **Clean Run Security Analyzer** - Clears the history of all ignored messages and warnings. It clears the ignored vulnerabilities which are marked as Ignore during the Run Security Analyzer and displays all vulnerabilities for the project
- **Clear Security Markers** - Removes all security warnings and resources. Run the security analyzer again to view the vulnerabilities for your resource

## Using the security analyzer

Follow the steps below to use Security Analyzer for your project folder or file:

1. Create a ColdFusion project or use an existing project
2. Ensure that the project is aligned to the preferred server. You can verify it by choosing the appropriate server in project properties. Right-click in the navigator and choose properties
3. Right-click the project folder or project file and choose Security Analyzer > Run Security Analyzer
4. Security analyzer analyzes the code and displays a popup dialog when the task is completed
5. Click OK
6. You can view all the vulnerabilities in the bottom pane of the Editor as shown below

![Vulnerabilities](Vulnerabilities.png)

1. Click Security Issues on the left pane to view the list of vulnerabilities
1. As shown in the left pane of the snapshot, click the vulnerability type such as SQL Injection or XSS attack to view the corresponding problem statement
1. You can also view the suggested solution at the right pane
1. Alternatively, you can click any error on the middle pane to view the corresponding statement and solution at the right pane
1. Double-click each error on the middle pane to view the corresponding line in the Editor
1. Use filters for File Name, Attack Name, Severity Level, and Type in the middle pane
1. Start typing the file name in the search area to locate the files with vulnerabilities
1. You can narrow down your search based on severity level as high, medium, and low by clicking All dropdown list

> **Note:** You can notice the Both dropdown list as grayed out sometimes. This happens when your cursor is already pointing to Errors or warnings issue type in the left pane. You can bring it back to active state by selecting the Security Issues folder.

When you fix the error in the code, right-click the corresponding error on the middle pane and choose the status as Fixed. Mark the status as Ignore if you ignore the error. You can move the error back to To fix status by using the same step.

> **Note:** Rerunning Security analyzer (Security Analyzer > Run Security Analyzer) does not show the vulnerabilities that are ignored. If the user has marked the vulnerabilities as Fixed but are not fixed, then server reports these errors.

Click Export on the upper-right corner of the Security Analyzer pane to export all the vulnerabilities to a report.html file. You can view the graphical representation of all vulnerabilities for your resource in the exported file as shown below:

![Graphical representation of vulnerabilities](Graphical-representation-of-vulnerabilities.png)

## Increasing the Security Analyzer timeout

You can increase the Security Analyzer timeout in the RDS Configuration settings. The default is 30 seconds.

1. Right click on the server or choose Windows > Show View > Other
2. Type RDS in the text field

## Additional setup configurations

Perform one of the following:

- Open access to port 8500 using the Windows firewall
- Set up a virtual directory for the site for CFIDE in IIS and the uri-worker-map.properties file for the given connector. In the file, remove the # in front of `/CFIDE=cfusion`

## Workflow of Security Analyzer

Security Analyzer is exposed as a service by the ColdFusion Server. By running Security Analyzer for a file or a set of files, the builder makes a request to this service. The builder displays the vulnerabilities in a separate view for each file along with corresponding line numbers. You can double-click on the vulnerabilities and open the file in the editor window with cursor pointing at the corresponding line with a red icon. Also, by single click you get a brief description about the attack and about possible ways to avoid it.

![Workflow](Workflow.png)

## List of security vulnerabilities

### SQL Injection

As shown in the following sample code, the attacker can create arbitrary SQL statements to execute against the database by passing values into the url.id variable. For example, the attacker can pass a value of "1; DELETE FROM news" to delete all news articles in the table, or "0 UNION SELECT username, password FROM users" to extract username and password values from the database.



#### Vulnerable scenarios

```
<cfset result = QueryExecute("select * from Employees where empid=#id#5")>

<cfset v3=form.vf>
<cfset employees = ORMExecuteQuery("from Employee where name=#v3#")>
```

All the above code samples use an unknown variable inside the query statement which makes them vulnerable.

### XSS Attack

```
<cfoutput>Hello #url.name#</cfoutput>
```

Using the above code, the attacker can pass JavaScript into the url.name variable to be executed in the browser of anyone visiting the URL. Attackers also try to post XSS code that can be stored in a database and execute later. For example, posting a comment to display for all visitors of a page.

#### Vulnerable scenarios

```
<cfoutput>Hello #name2#</cfoutput>

<cfparam name = "id12" default = "my default value" type="string">
<cfoutput>#id12#</cfoutput>
```

When a variable declared through cfparam is of type string, it is vulnerable code.

```
<cfoutput>
<b>LINK to URL</b> <a target="_blank" href="http://#url.url#"></a>
</cfoutput>
```

As an unknown variable is used for the url link in the anchor tag, it is vulnerable to XSS attack.

### PDF XSS Attack

The cfhtmltopdf tag introduced in ColdFusion 11 provides powerful HTML rendering powered by WebKit to produce PDF files. As the server renders the HTML, be cautious while using variables in the PDF document. All preventative measures pertaining to cross site scripting also apply to variables written in the cfhtmltopdf tag.

JavaScript can be executed during rendering in the cfhtmltopdf tag. Because the JavaScript would be executed on the server during rendering, the risks are different from a client side cross site scripting attack. Some of the risks include denial of service and potential exploit for unknown vulnerabilities in Webkit. In addition, there is a risk of bypassing the network firewall as the server can be behind a firewall with network access to other systems.

#### Vulnerable scenarios
