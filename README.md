# grep-between-multiple-lines
It's an AWK Script to quickly locate your complicated patterns according to your specific context.

## Installation
The only precondition is GNU AWK and shell environment.
### Steps
(Use Debian as Example)
sudo apt-get -y instal gawk

## Application
**Usage: gm [-c SCOPE] [-i] [-s] Pattern1 [Pattern2] [Pattern3]**
> Plus: you can put these options in whatever orders to make you feel really freely:)
- -i Ignorecase
- -s SmartCase
- -c The lines number of one side of searching context

Suggest to move 'gm' into your '/usr/local/bin/', give it execute permission, then you can:
```
kan@kan-x220i:~$gm ":sensorevent" "->enable" -c 30 period -i `find /work/daily/note/ -type f`
==========
<</work/daily/note/cts_sensor_timeout_and_wrong_order_on_msm8998.txt>>
1397@1:		status_t SensorService::SensorEventConnection::enableDisable(
1398-		        int handle, bool enabled, nsecs_t samplingPeriodNs, nsecs_t maxBatchReportLatencyNs,
1399-		        int reservedFlags)
1400-		{
1401-		    status_t err;
1402-		    if (enabled) {
1403@23:		        err = mService->enable(this, handle, samplingPeriodNs, maxBatchReportLatencyNs,
-----

```
