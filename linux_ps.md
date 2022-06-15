# The `ps` Command

The general syntax for the `ps` command is as follows:

```sh

ps [OPTIONS]

```

In it’s simplest form, when used without any option, `ps` will print four columns of information:

- `PID` - The process ID.

- `TTY` - The name of the controlling terminal for the process.

- `TIME` - The cumulative CPU time of the process, shown in minutes and seconds.

- `CMD` - The name of the command that was used to start the process.

  

## Common Options

The output above is not very useful as it doesn’t contain much information. The real power of the `ps` command comes when launched with additional options:

 
- `-e` option tells `ps` to display all processes.
- `-o` option allows you to specify which columns are displayed when running the `ps` command. Here is an explanation of useful details:

	1. `user` - The user who runs the process
	2. `comm` - The executable name
	3. `%cpu` - The cpu utilization of the process
	4. `%mem` - The percentage of the process’s resident set size to the physical memory on the machine
	5. `vsz` - Virtual memory size of the process in KiB
	6. `rss` - The size of the physical memory that the process is using
	7. `stat` - The the process state code, such as `Z` (zombie), `S` (sleeping), and `R` (running)
	8. `start` - The time when the command started

To adjust the width of each column explicit width is offered as `column:width`.

 
## Sorting the Output

  
The `ps` command also allows you to sort the output. For example, to sort the output based on the memory usage, you would use:

```sh
ps -e --sort=-%mem | head
```
