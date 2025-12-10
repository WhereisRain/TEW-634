# TEW-634

Exploit Author: yangchunyu@whu.edu.cn

Vendor: Trendnet

Firmware: TEW-634GRU_1.0R

There are three command injection vulnerabilities in this firmware vulnerability, and the vulnerabilities exist in the /sbin/httpd binary file of the firmware sample.

# system_time.cgi
The first command injection occurred in the "date" parameter of http://ip/system_time.cgi, as shown in the following figure.



# dns_query.cgi
The second command injection occurred in the "dns_query_name" parameter of http://ip/dns_query.cgi, as shown in the following figure.



# set_sta_enrollee_pin.cgi
The third command injection occurred in the "wps_sta_enrollee_pin" parameter of the URL http://ip/set_sta_enrollee_pin.cgi, as shown in the following figure.

