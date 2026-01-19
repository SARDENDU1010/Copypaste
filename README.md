100 - ((node_memory_MemAvailable_bytes{job=~"$JOB", instance=~"$instance"} / node_memory_MemTotal_bytes{job=~"$JOB", instance=~"$instance"}) * 100)

