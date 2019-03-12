###### v0.9

Overwatch
=========

System Load Average
---

As Linux administrator, on any sign of trouble with the system's health, __one critical state to monitor is the load average of the system__( this can be displayed with `uptime` or `top` commands ).

The __system load average__ is the number of processes that are either in a runnable or uninterruptable state, Unix refers to this as the run-queue length and basically is what we refer as CPU load, do not 
confused with CPU percentage. Load averages do not include any processes or threads waiting on I/O, networking, databases or anything else not demanding the CPU. It narrowly focuses on what is actively demanding CPU time. 

>A process in a runnable state is either using the CPU or waiting to use the CPU.
>A process in uninterruptable state is waiting for some I/O access, eg waiting for disk.
There are numerous ways of monitoring system load average including uptime. What does Overwatch is, it uses these tools and monitors given a interval of time any change in the load averages.

The three load-average values are the 1-minute, 5-minute and 15-minute average.  That means, reading from left to right, one can examine the aging trend and/or duration of the particular system state. for a more detailed information about this topic check the [Examining Load Average](https://www.linuxjournal.com/article/9001) article

Being monitoring all time the system health state is overwhelming although too demanding. So for this, i create __Overwatch__. 

__Overwatch__ monitors given some rules of thumbs, __last 5-minute average__. Why? Because is totally normal to have some spike above the healthy threshold over the one-minute average. The real pain is, when it becames a constant over the `5-minute` and the `15-minute` averages.

>Load averages are not normalized for the number of CPUs in a system, so a load average of 1 means a single CPU system is loaded all the time while on a 4 CPU system it means it was idle 75% of the time.

---

Report
---

Given the channels used for notifications I worked with, __overwatch__ send a notification to a slack webhook.

Usage
-----

Run it as daemon with 'watch'.

```shell
watch -n1 '~/bin/overwatch >> ~/log/overwatch.log' 2&>1 & 
```
