# ASP API Notes:

### HTTP REQUEST METHOD
The api can determine the http request method
```
Set method = Request.ServerVariables("REQUEST_METHOD") //POST, GET, etc
```

### REQUEST VALUES
The api can read posted form values and url query string values.
```
Set param = Request.QueryString("param")
Set field = Request.Form("field")
```

### HTTP RESPONSE CODES
The api should specify the http response codes.

```
//specifing the http status
response.Status = "200 Success"
response.Status = "401 Unauthorized"
response.Status = "400 Invalid Input"
```

### TERMINATING EARLY
The api can terminate the response early.
```
//terminate the response
Response.End
Response.Write("this output will never be written")
```
### READING HTTP HEADER
The api can read a request header.
```
//read a http request header of 'BON_API_KEY'
//which requires a prefix of 'HTTP_'
Set apiKey = Request.ServerVariables ('HTTP_BON_API_KEY')
```
### FUNCTIONS
ASP allows you to define functions. Return values are identified by the variable
with the same name as the function name.
```
Function myFnc(param1, param2)
    myFnc = "bazinga"
End Function
```

### INCLUDE SCRIPTS
ASP allows for the inclusion of other scripts.  All include scripts should
end with ASP if they are inside the web root folder.
```
<%
<!--#include file="time.asp"-->
%>
```
### AUTHENICATION
The api will be protected by a security token sent by the remote server in a http header

```
//getting header http header 'BON_API_KEY'
Set apiKey = Request.ServerVariables ('HTTP_BON_API_KEY')
If apiKey <> "my-secret-access-token" Then
    //client did not provide the secret access token, so terminate response
    response.Status = "401 Unauthorized"
    Response.End //end response early
End If

//continue with response
Response.Write("secure content goes here")
```
### CONTENT TYPE
The api should set the repsonse content type.

```
//setting response content type ('text/html', 'application/json')
Response.ContentType="application/json"
```
### JSON DATA FROMAT
The api should output json data.  The cleanest solution I have found is
[https://code.google.com/p/aspjson/](aspjson).

```
//outputting json ()
<!--#include file="JSON_latest.asp"-->

Dim json
Set json = jsObject()

json("name") = "Tuğrul"
json("surname") = "Topuz"
json("message") = "Hello World"

json.Flush
```

### PARAMETERIZED QUERIES (avoids SQL injections)
The api should use parameterized query inputs to avoid sql injections.  This topic is
discussed in length:

+   http://stackoverflow.com/a/12605019
+   http://stackoverflow.com/questions/149848/classic-asp-sql-injection-protection

```
Set input = "O'Brien"
Set sql = "INSERT dbo.Table(Column) values (?)"

Set cmd = CreateObject("ADODB.Command")
cmd.CommandText = sql
cmd.CommandType = adCmdText
cmd.ActiveConnection = conn
cmd.Parameters.Append(cmd.CreateParameter("@p1", adVarChar, adParamInput, 50, input))
cmd.Execute
Set cmd.ActiveConnection = Nothing
```

Another example found includes
```
Set input = "O'Brien"
Set sql = "update sometable set some_col=?"
Set cmd = CreateObject("ADODB.Command")
cmd.activeConnection = conn
cmd.commandText = sql
cmd.execute(, array(input))
```

So rewritten to support multiple inputs
```
//get inputs
Set firstname = Request.Form("firstname")
Set lastname = Request.Form("lastname")
Set inputs = array(firstname, lastname)

//setup sql
Set sql = "update sometable set firstname=?, lastname=?"

//setup command
Set cmd = CreateObject("ADODB.Command")
cmd.activeConnection = conn
cmd.commandText = sql

//execute sql
cmd.execute(, inputs)
```

### DATABASE PERFORMANCE

You should always get records from the database by using recordset.GetRows()
which returns a two dimension array.  Any other recordset function will make
round trips to the database. This includes just getting fields on a single row.
```
Set Products = cmd.Execute()
Dim arrProducts : Set arrProducts = Products.GetRows()

//just for fun get the number of rows and columns
dim cols : cols = ubound(arrProducts,1)
dim rows : rows = ubound(arrProducts,2)

//output json
Response.Write(toJSON(arrProducts))
```

### INPUT VALIDATION
You can validate inputs with functions:

+   isNull()
+   isEmpty()
+   isDate()
+   isNumeric()

### REFERENCES
+   [Request Methods](http://www.w3schools.com/asp/asp_ref_request.asp)
+   [Function Reference] (http://www.w3schools.com/vbscript/vbscript_ref_functions.asp)
+   [Looping] (http://www.w3schools.com/vbscript/vbscript_looping.asp)
