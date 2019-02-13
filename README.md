Overwatch
=========

The __system load average__ is the number of processes that are either in a runnable or uninterruptable  state, Unix refers to this as the run-queue length and basically is what we refer as __CPU load__.

- A process in a runnable state is either using the CPU or waiting to use the CPU.  
- A process in uninterruptable state is waiting for some I/O access, eg waiting for disk.

There are numerous ways of monitoring system load average including uptime. What does Overwatch is, it uses these tools and monitors given a interval of time any change in the load averages.

The averages are taken over the three time intervals, over the `last one-minute`, over the `last 5-minute` and over the `last 15-minute`.

Overwatch monitors over the last 5-minute, because is totally normal to have some spike above the healthy threshold on the one-minute average. its when it is a constant over the 5-minute and  the 15-minute averages we are in serious problem.

Load averages are not normalized for the number of CPUs in a system, so a load average of 1 means a single 
CPU system is loaded all the time while on a 4 CPU system it means it was idle 75% of the time.

Usage
-----

Run it as daemon with 'watch'.

```shell
watch -n1 '~/bin/overwatch >> ~/log/overwatch.log' 2&>1 & 
```
