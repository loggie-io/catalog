
## How to generate logs?

```
LOG_DIR ?= /tmp/log ## log directory
LOG_MAXSIZE ?= 10 ## max size in MB of the logfile before it's rolled
LOG_QPS ?= 0 ## qps of line generate
LOG_TOTAL ?= 5 ## total line count
LOG_LINE_BYTES ?= 1024 ## bytes per line
LOG_MAX_BACKUPS ?= 5 ## max number of rolled files to keep

./loggie genfiles -totalCount=${LOG_TOTAL} -lineBytes=${LOG_LINE_BYTES} -qps=${LOG_QPS} \
	-log.maxBackups=${LOG_MAX_BACKUPS} -log.maxSize=${LOG_MAXSIZE} -log.directory=${LOG_DIR} -log.noColor=true \
	-log.enableStdout=false -log.enableFile=true -log.timeFormat="2006-01-02 15:04:05.000"
```

example:

```
# Generate a log file loggie.log under /tmp/log, 
# which contains 1000 logs, each line of log is 1KB, and the total size is about 1.1MB

./loggie genfiles -totalCount=1000 -lineBytes=1024 -qps=0 \
	-log.maxBackups=1 -log.maxSize=1000 -log.directory=/tmp/log -log.noColor=true \
	-log.enableStdout=false -log.enableFile=true -log.timeFormat="2006-01-02 15:04:05.000"
```
