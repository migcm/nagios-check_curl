# nagios-check_curl
Check a web page contents for specific search terms. Built on [check_curl2](https://exchange.nagios.org/directory/Plugins/Websites,-Forms-and-Transactions/check_curl2/) posted on Nagios Exchange by nagiosexchange. Added capability to define authentication type, number of apparitions of Grep, header values, HTTP expected code, etc.


### Syntax and options:
    -U URL (s)
    -A Agent (s)(default: Mozilla/5.0 ... )
    -a Authentication (s)(example: '[user]:[password]')
    -ao Authentication method to use (example: 'CURLAUTH_DIGEST')
    -G Grep page on STRING (s)(can be set multiple times)
    -Gn Number of apparitions of Grep
    -he Any other tags to be sent in http header. Use multiple times for additional headers (example: 'X-Requested-Auth: Digest')
    -L Show page (-)
    -F Follow redirects (-)
    -I Ignore SSL certificate errors (-)
    -X Exclude performance data (default: include)
    -Tc Critical page return time (i)
    -Tw Warning page return time (i)
    -Sbc Critical page size below SIZE (i)
    -Soc Critical page size over SIZE (i)
    -Sbw Warning page size below SIZE (i)
    -Sow Warning page size over SIZE (i)
    -S Find string between ARG1 and ARG2, return first match (s s) (example: value=\" \" )
    -T Timeout (i)(default: 10sec)
    -O Output Driven Check - Page Should respond with \"Status: OK\" or otherwise
    -hc HTTP expected code (default: 200)


### Examples:
```check_curl -U http://test.example.net";```

```check_curl -U http://test.example.net:8888/info -he 'X-Requested-Auth: Digest' -ao CURLAUTH_DIGEST -a "USER:PASSWORD" -G searchme -G searchme2```

```check_curl -U http://test.example.net:8888/info -a "USER:PASSWORD" -G "<status>0</status>" -Gn 5```
