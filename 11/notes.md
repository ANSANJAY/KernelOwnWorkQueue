WQ_SYSFS
-------------

A given workqueue can be made visible in the sysfs filesystem by passing the WQ_SYSFS to that workqueue's alloc_workqueue()

$ ls sys/devices/virtual/workqueue


# echo 1 > /sys/devices/virtual/workqueue/cpumask

