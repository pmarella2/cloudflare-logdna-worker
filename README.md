# cloudflare-dnalog-worker (modified by pmarella2)
A cloudflare worker script to forward logs to [logdna](https://logdna.com/)

## How to use
1. Naviagate to index.js and copy it contents
2. Change yourAppName and yourHostName to your app name and host name, read the logdna [Ingest API](https://docs.logdna.com/v1.0/reference#api)
* You can also change maxRequestsPerBatch - it dictates how many maximum requests to batch per export, by default it is set to send all the batched requests once per 10 seconds
3. Paste it into your worker editor in cloudflare

## About compiledPass

you should precompile your logdna ingestion key and store it in the compilePass parameters, you can simply type in console `btoa(username+':'+password)` where username is your ingestion key and password keep empty, and put the results into the parameter to save some cpu time(probably)


I left all the console.log command to better help you debug

### logged parameters:

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
