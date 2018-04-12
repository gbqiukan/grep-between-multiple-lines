# Grep between your particular context
Once the demand for searching become complex, it is painful when you only have tools to grep out of one line.
It's a draft AWK Script to quickly locate your complicated patterns according to your specific context.
AWK also has support for extended regular expression:)

## Installation
The only precondition is GNU AWK and shell environment.

### Steps
(Use Debian as Example)
sudo apt-get -y install gawk

## Application
**Usage: gm [-c SCOPE] [-i] [-s] Pattern1 [Pattern2] [Pattern3]**
> Plus: you can put [-c SCOPE], [-i], [-s] and [Pattern] options in whereever and whatever orders which would make you feel the most freely:)
- -i IgnoreCase
- -s SmartCase
- -c The lines number of one side of searching context, the default is 1.
- Also can freely use only two [pattern] as key words for describing your specific context. Also only one pattern is OK.

Suggest to move 'gm' into your '/usr/local/bin/', give it permission to execute, then you can find out your particular context within multiple lines now.

For example, you need find out a function whose class name starts with 'sensorservice', and it should contains one calling looks like '->enable', then you think it should exist 'period' as the key word in the same or next or very near lines:
```
kay@home:~$gm "\<sensorservice" "->enable" period -i -c 200 `find /work/daily/note/ -type f`
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
