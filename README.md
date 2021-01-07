# cloudflare-logdna-worker (modified by pmarella2)
A cloudflare worker script to forward logs to [logdna](https://logdna.com/)

## How to use
1. Naviagate to index.js and copy it contents
2. Change `yourIngestionKey` and `yourHostName` to your ingestion key and host name, read the logdna [Ingest API](https://docs.logdna.com/v1.0/reference#api)
* You can also change `maxRequestsPerBatch` - it dictates how many maximum requests to batch per export, by default it is set to send all the batched requests once per 10 seconds
3. Paste it into your worker editor in cloudflare

## Logged parameters
+ user agent
+ referer
+ ip
+ countryCode
+ url
+ colo
+ workerInception
+ workerId
+ method
+ x_forwarded_for
+ asn
+ status
+ originTime
+ CF-Cache-Status
+ CF-Ray
+ tlsCipher
+ tlsVersion
+ clientTrustScore

## Log export format
```
data.meta.ip + " - - " + data.meta.method + " | " + data.meta.status + " | " + data.meta.url + " | " + data.meta.ua + " | " + data.meta.referer + " | " + data.meta.x_forwarded_for;
```

## Sample log ingested from the worker
<p align="center">
  <img src="https://github.com/pmarella2/cloudflare-logdna-worker/blob/master/Log_Format.png?raw=true" alt="Log Format"/>
</p>

```
{
  "ua": "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:62.0) Gecko/20100101 Firefox/62.0",
  "referer": "empty",
  "ip": "54.38.134.219",
  "countryCode": "FR",
  "colo": "CDG",
  "workerInception": 1605428892780,
  "workerId": "97VRQS",
  "url": "http://praneethmarella.xyz/wp-login.php",
  "x_forwarded_for": "0.0.0.0",
  "asn": 16276,
  "cfRay": "5f2798f3ba01ee2b",
  "tlsCipher": "",
  "tlsVersion": "",
  "originTime": 19,
  "cfCache": "DYNAMIC",
  "raw": {
    "cf": {
      "clientTcpRtt": 30,
      "tlsVersion": "",
      "httpProtocol": "HTTP/1.1",
      "tlsCipher": "",
      "edgeRequestKeepAliveStatus": 1,
      "requestPriority": "",
      "country": "FR",
      "clientAcceptEncoding": "gzip",
      "colo": "CDG",
      "tlsClientAuth": "{\n  \"certIssuerDNLegacy\": \"\",\n  \"certIssuerDN\": \"\",\n  \"certIssuerDNRFC2253\": \"\",\n  \"certSubjectDNLegacy\": \"\",\n  \"certNotAfter\": \"\",\n  \"certVerified\": \"NONE\",\n  \"certFingerprintSHA1\": \"\",\n  \"certSubjectDN\": \"\",\n  \"certFingerprintSHA256\": \"\",\n  \"certNotBefore\": \"\",\n  \"certSerial\": \"\",\n  \"certPresented\": \"0\",\n  \"certSubjectDNRFC2253\": \"\"\n}",
      "asn": 16276
    },
    "fetcher": {},
    "redirect": "manual",
    "headers": {},
    "url": "http://praneethmarella.xyz/wp-login.php",
    "method": "GET",
    "bodyUsed": false,
    "body": null
  },
  "_method": "GET",
  "_status": 308
}
```
