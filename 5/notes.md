WQ_HIGHPRI
-------------

This flag is used to mark a workqueue as high priority

Queued to the highpri worker-pool of the target cpu.

Highpri worker-pools are served by worker threads with elevated nice level.

Nice value: 
------------



Nice value ranges from -20 (highest priority level) to 19 (lowest priority level)

Default value is 0.

To check the nice value:

$ ps ax -o pid,ni,cmd

The above command prints pid, nice value and process name
