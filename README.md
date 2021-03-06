# CPU Profiler in Linux

This Linux kernel module perftop keeps track of the time spent on the CPU and the corresponding call stack for each task. The module displays the profiling result using the `proc` file system. It displays the top 20 tasks that spend with respect to time spent on the CPU. The module uses a red-black tree to monitor tasks and their corresponding statistics. The module uses `kretprobes` to probe the `pick_next_task_fair` function of CFS Scheduler and get the task that is scheduled next.

To compile the module, run the `make` command. Once compiled, the output file generated is `perftop.ko`.

Running the module:

1. Insert the module using the command `sudo insmod perftop.ko`.
2. After module has been inserted successfully, run `cat /proc/perftop`.
3. The output of the profiler will be displayed. `dmesg` can be used to look at module insertion status.

To remove the module, run `sudo rmmod perftop`.
