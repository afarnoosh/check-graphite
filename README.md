check_graphite is a nagios module to query graphite

## Example

check_graphite -H 'http://my.graphite.host

check_graphite  -H "http://your.graphite.host/render" -M collectd.somebox.load.load.midterm  -w 1 -c 2 -N load
WARNING|load=1.4400000000000002;;;;

check_graphite accepts the following options:

* `-H` or `--endpoint`: the graphite HTTP endpoint which can be queried
* `-M' or `--metric`: the metric expression which will be queried, it can be an expression
* `-F` or `--from`: time frame for which to query metrics, defaults to "30seconds"
* `-N` or `--name`: name to give to the metric, defaults to "value"
* `-w`: warning threshold for the metric
* `-c`: critical threshold for the metric
* `-t`: timeout after which the metric should be considered unknown

## How it works

check_graphite, asks for a small window of metrics, and computes an average over the last valid
points collected, it then checks the value against supplied thresholds.

NaN values are not taken into account in the average
