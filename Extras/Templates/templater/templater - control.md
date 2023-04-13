<%* if (tp.file.title == "MyFile" ) { -%>
This is my file!
<%* } else { -%>
This isn't my file!
<%* } -%>
Some content ...


<%* if (tp.date.now("ddd") == "Sat" | "Sun") { %>
- [ ] 建立 Weekly Note 
<%* } { %>

<%* } %>

https://silentvoid13.github.io/Templater/commands/whitespace-control.html