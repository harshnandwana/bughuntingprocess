process of working:

1. whatweb:		`whatweb <domain>| grep "200 OK"`
2. gospider		`gospider -s "$domain" -o output -t 10`
3. search for robots.txt and sitemap.xml
4. url lfi
	* `../../../etc/passwd%00`
	* `....//....//....//etc/passwd`
	* `%252e%252e%252fetc%252fpasswd`
5. add target to scope in burp and start spider/crawler
6. if CMS=wordpress check `wpscan <url>` 
7. go for wayback machine and search last update
8. try nikto for vulnerability
9. try nuclei
10. take eye on source code for type of protocol used 
11. check for file upload portal
12. categories site in a type ie blog/e-commerce/finance/etc.
13. if possible register an account and try:
	1. changing password and intercepting the request and removing current password
	2. clickjacking
	3. try registering new username by giving space in starting " uname"
	4. note the url after login and try changing values of user, any uploaded document to browse through unauth content
	5. try using this url to enter unauthorized places containing edit feature by changing 'Referer:'
14. try editing js and css file or add new files
	* e-commerce
		1. try changing value of product in burp
		2. try replacing value of high cost prod with low cost prod
		3. view for viewstate header and try decoding base 64
		4. try adding a discount coupon and intercept the request made, select do intercept response and try editing response from server
		5. try editing request made to the payment portal
		6. search for disable element in source code or server reponse
		7. try changing referer for as most sites and changing referer to admin
		8. try registering new username by giving space in starting " uname"
	* blog  
		1. search for hidden login page 
		2. try authentication breakdown
		3. try xss and icors wherever possible
		5. weak password policy
		6. use xsstrike against search domain
		7. try remote file inclusion
15. use forgot password for username enumeration
	* also try forgetting passwords from various accounts and try to find any similarities
16. if remember me is turned on intercept request and check for `RememberUser=<daf>` inn cookies
	* if cookie is encrypted try using it for various accounts and decipher the text
17. try priveleage escalation
	* try URL /admin/ImpersonateUser.jsp as this may make web app think that an admin is trying to access the data. given you must know the username and other essential details.
	
	
