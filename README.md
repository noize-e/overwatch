Overwatch
=========

In every linux server, the load average is a critical metric to messaure the system's health.

```#bash
root@localhost:~# uptime
 17:46:36 up 9 days,  8:19,  1 user,  load average: 0.00, 0.00, 0.00
```

The load average is the number of processes that are running or uninterruptible; the run-queue length  or CPU load.
This metric doesn't include processes/threads waiting in I/O, networking and databases. It narrowly focuses on what is actively demanding CPU time. 
A process in a runnable state is either using the CPU or waiting to use the CPU. In a uninterruptible state is waiting for I/O access. 

Overwatch monitor this metric relying in the uptime's output.

## Usage

```bash
chmod x-ug ~/bin/overwatch
watch -n1 '~/bin/overwatch >> ~/log/overwatch.log' 2&>1 &
```

### Notification:
![slack-report](https://github.com/noize-e/overwatch/blob/master/overwatch-report.png)

