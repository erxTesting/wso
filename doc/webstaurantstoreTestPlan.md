# webstaurantstore  - Test Plan

## Communication
- Email / GitHub

## Environment
- Production in-house ecommerce site https://www.webstaurantstore.com/ specifically the Outlet functionality.  Exclude third-party calls e.g. Facebook, twitter, google unless calls are essential to page components.  (recommend environment component, tier, scale descriptions to be added for future testing)

## Data
- Existing data for production site CMS, no additional test data to be added.  

## Transactions
- Scratch & Dent Outlet "Outlet" products, random products.  
- No geolocation distribution, single load agent US east coast calls

## Tests
- Load
  - The load test should run with a maximum of 5 RPM for a duration of 15 minutes, using a randomized sampling of
product pages.
  - ~~Begin with a limit of 1 transaction per minute, then increase by 1 transaction per minute, up to a maximum of 5 transactions per minute.~~
- Stress; n/a
- Capacity; n/a
- Endurance; n/a
- Volume; n/a
- Spike; n/a

## Tools
- JMeter 5.6.3 https://jmeter.apache.org/download_jmeter.cgi
- BlazeMeter - Taurus https://github.com/Blazemeter/taurus
- AWS Cloud9 m5.large (8 GiB RAM + 2 vCPU) Amazon Linux 2023

## Monitoring
- App; HTTPS calls to site, JMeter monitors https://jmeter.apache.org/usermanual/glossary.html
  - Elapsed time. JMeter measures the elapsed time from just before sending the request to just after the last response has been received. JMeter does not include the time needed to render the response, nor does JMeter process any client code, for example Javascript.
  - Latency. JMeter measures the latency from just before sending the request to just after the first response has been received. Thus the time includes all the processing needed to assemble the request as well as assembling the first part of the response, which in general will be longer than one byte. Protocol analysers (such as Wireshark) measure the time when bytes are actually sent/received over the interface. The JMeter time should be closer to that which is experienced by a browser or other application client.
  - Connect Time. JMeter measures the time it took to establish the connection, including SSL handshake. Note that connect time is not automatically subtracted from latency. In case of connection error, the metric will be equal to the time it took to face the error, for example in case of Timeout, it should be equal to connection timeout.
  - Median is a number which divides the samples into two equal halves. Half of the samples are smaller than the median, and half are larger. [Some samples may equal the median.] This is a standard statistical measure. See, for example: Median entry at Wikipedia. The Median is the same as the 50th Percentile
  - 90% Line (90th Percentile) is the value below which 90% of the samples fall. The remaining samples too at least as long as the value. This is a standard statistical measure. See, for example: Percentile entry at Wikipedia.
  - Standard Deviation is a measure of the variability of a data set. This is a standard statistical measure. See, for example: Standard Deviation entry at Wikipedia. JMeter calculates the population standard deviation (e.g. STDEVP function in spreadsheets), not the sample standard deviation (e.g. STDEV).
  - Recommend incorporating infra and app specific for future testing. 
- Database; n/a recommend incorporating infra and db specific for future testing. 
- Logging; no system access.  