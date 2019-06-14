#### What does “|&” mean in bash?

From `man 1 bash`, section **Pipelines**:

> If |& is used,
command's  standard  error, in addition to its standard output, 
is connected to command2's standard input through the pipe

So it is just like pipe operator `|`, but piping both stdout and stderr.
