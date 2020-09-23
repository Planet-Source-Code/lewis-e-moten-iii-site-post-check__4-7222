<div align="center">

## Site Post Check


</div>

### Description

Checks the HTTP Referer header to ensure people are not posting from other websites. You can include this file if you use templates on your website, or just include it on the pages that receive form data posts.

Warning - someone who knows there stuff can get around this by modifying there HOST file. this isn't 100% fool proof, but it may deter most from posting data from other websites.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Lewis E\. Moten III](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/lewis-e-moten-iii.md)
**Level**          |Advanced
**User Rating**    |5.0 (20 globes from 4 users)
**Compatibility**  |ASP \(Active Server Pages\)
**Category**       |[Security](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/security__4-14.md)
**World**          |[ASP / VbScript](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/asp-vbscript.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/lewis-e-moten-iii-site-post-check__4-7222/archive/master.zip)





### Source Code

```
<%
Call SitePostCheck()
Sub SitePostCheck()
	Dim lblnPost		' user posted data to page?
	Dim lstrReferer		' page user is comming from
	Dim lstrHost		' server user is on
	lblnPost = Request.ServerVariables("REQUEST_METHOD") = "POST"
	' if data wasn't posted, everythign is ok
	If Not lblnPost Then Exit Sub
	lstrReferer = Request.ServerVariables("HTTP_REFERER")
	lstrHost = Request.ServerVariables("HTTP_HOST")
	' If user is posting from antoher website
	If InStr(1, lstrReferer, "//" & lstrHost & "/", vbTextCompare) = 0 Then
		%>
		<H1><FONT color="red">Security Alert</FONT></H1>
		<P>
			The security of this web site does not allow you to post
			data from other websites.
		</P>
		<%
		Response.End
	End If
End Sub
%>
```

