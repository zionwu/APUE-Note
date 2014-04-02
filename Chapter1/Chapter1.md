##Chapter 1 Unix System Overview  
####1. Logging In 
* The entry in /etc/passwd is composed of 7 colon-separated fields: the login name, encrypted password, numeric user ID, numeric group ID, a comment field, home directory and shell program.  
Example:  
> sar:x:205:105:Zion Wu:/home/ziwu:/bin/csh  

####2. Files and directories
* A directory entry is a file that contains directory entries. Logically, we can think of each directory entry as containing a filename along with a structure of information describing  the attributes of the file. The **stat** and **fstat** function return a structure of information containing al the attributes of a file.

* The only two characters that can not appear in the filename are the slash(/) and the null character.

####3. Input and Output
* File descriptor are normally small non-negative integers that the kernel uses to identify the files being accessed by a particular process.

####4. Programms and Processes 
* every process has a unique numeric identifier called the process ID, which is always a non-negative integer.
* **execlp** function wants a null-terminated argument, not a newline-terminated argument.
* **fork** returns the non-negative process ID of the new child process to the parents, and returns 0 to the child.
* All the threads within a process share the same address space, file descriptors, stacks, and process-realted attributes. Because they can access the same memory, the threads need to synchronize access to shared data to avoid inconsistencies.
* Threads ID are local to a process. A thread ID from one process has no meaning in another process.

####5. Error Handling
* The file **error.h** defines the symbol errno and constants for each value that errno can assume. Each of these constants begins with "E". 
* There are two rules to be aware of with respect to errno. First, its value is never cleared by a routine if an error does not occur. Therefore, we should examine its value only when the return value from a function indicates that an error occurred. Second, the value of errno is never set to 0 by any of the fucntion.
* The errors defined in **error.h** can be divided into two categories: fatal and nonfatal.
* Resourse-related nonfatal errors include EAGAIN, ENFILE, ENOBUFS, ENOLCK,  ENOSPC, ENOSR, EWOULDBLOCK and sometimes ENOMEM, EBUSY can be treated as a nonfatal error when it indicates that a shared resource is in use.

####6. Signals
* Signals are a technique used to notify a process that some condition has occurred.
