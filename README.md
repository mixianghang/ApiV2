# ThreatCrowd API v2 ![ThreatCrowd](https://www.threatcrowd.org/img/home.png  "ThreatCrowd")
The ThreatCrowd API allows you to quickly identify related infrastructure and malware.

# Objects 
With the ThreatCrowd API you can search for:
- Domains
- IP Addreses
- E-mail adddresses
- Filehashes
- Antivirus detections

# Examples
You can download a  [sample python application](https://github.com/threatcrowd/ApiV2/blob/master/PythonExample/threatcrowd.py), a [sample C# application](https://github.com/threatcrowd/ApiV2/tree/master/CSharpExample) and a [sample javascript application](http://jsfiddle.net/f60unkz1/). 

# API Requests
The request and response format is similiar to that of the VirusTotal API - this is to allow for code reuse. 
HTTP GET requests are used to return JSON objects, for example:

- https://www.threatcrowd.org/searchApi/v2/email/report/?email=william19770319@yahoo.com
- https://www.threatcrowd.org/searchApi/v2/domain/report/?domain=aoldaily.com
- https://www.threatcrowd.org/searchApi/v2/ip/report/?ip=188.40.75.132
- https://www.threatcrowd.org/searchApi/v2/antivirus/report/?antivirus=plugx


For example, the following python code:
```
import requests, json
result =  requests.get("https://www.threatcrowd.org/searchApi/v2/email/report/", params = {"email": "william19770319@yahoo.com"})
print result.text

j = json.loads(result.text)
print j['domains'][0]
```

Would print:
```
{"response_code":"1","domains":["aoldaily.com","aunewsonline.com","cnndaily.com","usnewssite.com"],"references":[],"permalink":"https:\/\/www.threatcrowd.org\/email.php?email=william19770319@yahoo.com"}

aoldaily.com
```

# About
The previous version of the API (http://threatcrowd.blogspot.co.uk/p/api.html) is deprecated but the endpoint is still active.
Maltego transforms (http://threatcrowd.blogspot.co.uk/p/threatcrowd-maltego-transform.html) are also available.

The Search API is designed to identify results, rather than provide detailed information.
For detail please review the search results, or APIs (such as VirusTotal , TotalHash and PassiveTotal).

# Limits
Please limit all requests to one every ten seconds. To maintain perforamnce, IP addresses that don't adhere to this may be banned.

# Terms and Conditions
I make no guarantees as to the availability or veracity of results.
Additionally, all information is provided "as is" and I disclaim all warranties.
All access to the server is logged.
