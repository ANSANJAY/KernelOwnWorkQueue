Other Flags
-------------

WQ_FREEZABLE:

	A freezable wq participates in the freeze phase of the system  suspend operations.
	This flag is used in the context of power management and file systems, and is especially important for creating the system image in the suspend phase
	workqueues which can run tasks as part of the suspend/resume process should not have this flag set.
	You can find more information about this topic in Documentation/power/freezing-of-tasks.txt.


WQ_MEM_RECLAIM:
	
	All workqueues which might be used in the memory reclaim paths must have this flag set.
	The workqueue is guaranteed to have at least one woker, a so-called rescuer thread, regardless of memory pressure.
	Let us consider the following scenario:
		Workqueue W has 3 items A, B and C.

		A does some work and then waits until C has finished some work.
		
		Afterwards, B does some GFP KERNEL allocations and blocks as there is not enough memory available.
	
		As a result, C cannot run since B still occupies the W's worker;

		another worker cannot be created because there is not enough memory.

		A pre-allocated rescuer thread can solve this problem, by executing C which then wakes up A.

		B will continue as soon as there is enough available memory to allocate.

WQ_CPU_INTENSIVE:

		tasks on this workqueue can be expected to use a fair amount of CPU time.

		In other words, runnable CPU intensive work items will not prevent other work items in the same worker pool from starting execution.




