pgrep, proccess status, threads info.
-----

```
_pgrep(){
  ps ax | grep $1 | sed "/grep $1/{d}" | awk '{print $1}'
}
_processStatus(){
  _pid=$(_pgrep $1)
  [ -n "$_pid" ] && cat /proc/$(_pgrep $1)/status
}
_processThreads(){
  _processStatus $1 | grep -i thread
}
```



