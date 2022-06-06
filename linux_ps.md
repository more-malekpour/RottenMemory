# The `ps` Command
The general syntax for the `ps` command is as follows:
```sh
ps [OPTIONS]
```
In it’s simplest form, when used without any option, `ps` will print four columns of information:
-   `PID` - The process ID.
-   `TTY` - The name of the controlling terminal for the process.
-   `TIME` - The cumulative CPU time of the process, shown in minutes and seconds.
-  `CMD` - The name of the command that was used to start the process.

## Common Options
The output above is not very useful as it doesn’t contain much information. The real power of the `ps` command comes when launched with additional options:

- `a` option tells `ps` to display the processes of all users.
- `u` stands for a user-oriented format that provides detailed information about the processes.
- `x` option instructs `ps` to list the processes without a controlling terminal. Those are mainly processes that are started on boot time and running in the background.
- `f` option tells `ps` to display a tree view of parent to child processes:

The command `ps aux` displays information in eleven columns labeled `USER`, `PID`, `%CPU`, `%MEM`, `VSZ`, `RSS`, `STAT`, `START`, `TTY`, `TIME`, and `CMD`.

```output
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.8  77616  8604 ?        Ss   19:47   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    19:47   0:00 [kthreadd]
...
```

Here is an explanation of labels:
-   `USER` - The user who runs the process.
-   `%CPU` - The cpu utilization of the process.
-   `%MEM` - The percentage of the process’s resident set size to the physical memory on the machine.
-   `VSZ` - Virtual memory size of the process in KiB.
-   `RSS` - The size of the physical memory that the process is using.
-   `STAT` - The the process state code, such as `Z` (zombie), `S` (sleeping), and `R` (running).
-   `START` - The time when the command started.

## Sorting the Output

The `ps` command also allows you to sort the output. For example, to sort the output based on the memory usage, you would use:
```sh
ps aux --sort=-%mem | head
```
## User-defined Format
The `o` option allows you to specify which columns are displayed when running the `ps` command. For example, to print information only about the `PID`, `%MEM`, and `COMMAND`, you would run one of the following commands:
```sh
ps axo pid,%mem,comm --sort=-%mem | head
```
