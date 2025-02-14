## DNS  
  
Processing order:

hosts > DNS  
  
**/etc/hosts** - local hosts file  
**cat /etc/resolv.conf** - specify nameserver  
nameserver = 192.168.1.100  
  
If you have an entry in both places, hosts takes priority over DNS. This order can be changed via the file below:  
  
**cat /etc/nsswitch.conf** - edit this file to change processing of DNS  
"hosts: files dns"  
  
Anything not in your nameserver or your hosts file will not resolve. To fix this, use an additional nameserver in /etc/resolv.conf  
  
Additionally you can configure your DNS server to forward any unknown host names to other nameservers on the internet, i.e. 8.8.8.8 so it can resolve when it doesn't have an entry.  
  
## Understanding Domains  
  
[www.google.com](http://www.google.com/)  
  
**.** - root domain  
  
**.com** - top level domain  
  
**google** - domain name  
  
**www or drive or maps or apps** - subdomain  
  
**.edu or .com or .net or .org or .io** - Top Level Domains; TLDs

Example: apps.google.com

DNS goes out through internal DNS server, then forwards request to the internet:

1. Your DNS server
2. Root DNS (.)
3. DNS points you to a server serving up .com addresses (.com)
4. DNS points you to a server serving up the subdomain (Google)
5. Googles DNS server now gives you the IP for the apps server i.e. 216.58.221.76

Servers then cache this for a point in time so it doesn't have to go back out to the internet. 

When on network, requesting "web", you can simply search this by the fully qualified or you can append the etc/resolv.conf file on your internal DNS server, so it always appends the domain when you do NS lookups. I.e.

**cat >> /etc/resolv.conf**  
nameserver - 192.168.1.100
search - mycompany.com

Now whenever you search for a server on your internal network, say web.mycompany.com, the search will automatically append the mycompany.com to the record without you specifying it.

You also can utilize multiple domains, so:

search - mycompany.com prod.mycompany.com

Record Types stored in nameservers

**A Record**  - Web-server - IPv4 Address - 192.168.1.1
**AAAA Record** - Web-server - IPv6 Address - 2001:0db8:85a3:0000:0000:8a2e:0370:7334
**CNAME** - food.web-server - can contain multiple aliases - eat.web-server, hungry.web-server

Nslookup will only query stuff in your DNS server, it will not query stuff in the local hosts file. 

Dig is a powerful tool for looking at DNS records. 