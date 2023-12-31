kworker
-----------

kworker processes are kernel worker processes

From Documentation/kernel-per-CPU-kthreads.txt,

Naming convention: kworker/%u:%d%s (cpu, id, priority)

Worker threads are also two types:

	CPU Bound  : It is named as kworker/<corenumber>:<id>
	CPU Unbound: It is named as kworker/u<poolnumber>:<id>

$ ps -ef | grep 'kworker'

kworker/2:0H      -->   running on CPU2 and threadID 0 and is high priority bounded

The u designates a special CPU, the unbound cpu, meaning that the kthread is currently unbound
kworker/u257:0-   -->   unbound thread runs on any CPU

Use taskset to find the CPU Affinity
------------------------------------

taskset is used to set or retrieve the CPU affinity of a running process given its PID or to launch a new COMMAND with a given CPU affinity.

$ taskset -p [PID]


To find out what any kworker is doing
-------------------------------------

$ cat /proc/$(pid_of_kworker)/stack
