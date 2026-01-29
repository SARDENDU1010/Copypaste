100 - (
  windows_logical_disk_free_bytes{
    job="$JOB",
    instance="$instance",
    volume!~"HarddiskVolume.*"
  }
  /
  windows_logical_disk_size_bytes{
    job="$JOB",
    instance="$instance",
    volume!~"HarddiskVolume.*"
  }
) * 100

