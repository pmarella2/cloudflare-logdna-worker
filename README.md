# cloudflare-dnalog-worker (modified by pmarella2)
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
