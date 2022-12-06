# PromQL

## Selecting series

Select latest sample for series with a given metric name:

```bash
node_cpu_seconds_total
```

Select 5-minute range of samples for series with a given metric name:

```bash
node_cpu_seconds_total[5m]
```

Only series with given label values:

```bash
node_cpu_seconds_total{cpu="0",mode="idle"}
```

Select data from one day ago and shift it to the current time:

```bash
process_resident_memory_bytes offset 1d
```

## Rates of increase for counters

Per-second rate of increase, averaged over last 5 minutes:

```bash
rate(demo_api_request_duration_seconds_count[5m])
```

Per-second rate of increase, calculated over last two samples in a 1-minute time window:

```bash
irate(demo_api_request_duration_seconds_count[1m])
```

Absolute increase over last hour:

```bash
increase(demo_api_request_duration_seconds_count[1h])
```

## Aggregating over multiple series

Sum over all series:

```bash
sum(node_filesystem_size_bytes)
```

Preserve the instance and job label dimensions:

```bash
sum by(job, instance) (node_filesystem_size_bytes)
```

Aggregate away the instance and job label dimensions:

```bash
sum without(instance, job) (node_filesystem_size_bytes)
```

## Aggregating over time

Average within each series over a 5-minute period:

```bash
avg_over_time(go_goroutines[5m])
```

Get the maximum for each series over a one-day period:

```bash
max_over_time(process_resident_memory_bytes[1d])
```

Count the number of samples for each series over a 5-minute period:

```bash
count_over_time(process_resident_memory_bytes[5m])
```

## Time

Get the age of the last successful batch job run:

```bash
time() - demo_batch_last_success_timestamp_seconds
```

Find batch jobs which haven't succeeded in an hour:

```bash
time() - demo_batch_last_success_timestamp_seconds > 3600
```

## Subqueries

Calculate the 5-minute-averaged rate over a 1-hour period, at the default subquery resolution (= global rule evaluation interval):

```bash
rate(demo_api_request_duration_seconds_count[5m])[1h:]
```

Calculate the 5-minute-averaged rate over a 1-hour period, at a 15-second subquery resolution:

```bash
rate(demo_api_request_duration_seconds_count[5m])[1h:15s]
```

Using the subquery result to get the maximum rate over a 1-hour period:

```bash
max_over_time(
  rate(
    demo_api_request_duration_seconds_count[5m]
  )[1h:]
)
```

## Thanks

Thanks to PromLabs for there incredible work. All the info's on this page come from [here](https://promlabs.com/promql-cheat-sheet/).
