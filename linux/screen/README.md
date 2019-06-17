#### Screen Notes

---

##### Basic usage

---

```
# screen -S <session name> -s <shell>
screen -S 1 -s bash
```

##### Check you screen

---

```
echo $STY
```

##### List all screen sessions

---

```
screen -ls
```

##### In screen usage

---

`Ctrl + a`  is prefix key. 

`Ctrl + a`, then `?` is help. 

`Ctrl + a`, then `c` to create a new window

`Ctrl + a`, then `'` enter a number to select a window after prompt. 

`Ctrl + a`, then `"` select a window by list. 

`Ctrl + a`, then `n` or `p` to go to next or previous window. 


##### Command Help

```
Use: screen [-opts] [cmd [args]]
 or: screen -r [host.tty]

Options:
-4            Resolve hostnames only to IPv4 addresses.
-6            Resolve hostnames only to IPv6 addresses.
-a            Force all capabilities into each window's termcap.
-A -[r|R]     Adapt all windows to the new display width & height.
-c file       Read configuration file instead of '.screenrc'.
-d (-r)       Detach the elsewhere running screen (and reattach here).
-dmS name     Start as daemon: Screen session in detached mode.
-D (-r)       Detach and logout remote (and reattach here).
-D -RR        Do whatever is needed to get a screen session.
-e xy         Change command characters.
-f            Flow control on, -fn = off, -fa = auto.
-h lines      Set the size of the scrollback history buffer.
-i            Interrupt output sooner when flow control is on.
-l            Login mode on (update /var/run/utmp), -ln = off.
-ls [match]   or
-list         Do nothing, just list our SockDir [on possible matches].
-L            Turn on output logging.
-m            ignore $STY variable, do create a new screen session.
-O            Choose optimal output rather than exact vt100 emulation.
-p window     Preselect the named window if it exists.
-q            Quiet startup. Exits with non-zero return code if unsuccessful.
-Q            Commands will send the response to the stdout of the querying process.
-r [session]  Reattach to a detached screen process.
-R            Reattach if possible, otherwise start a new session.
-s shell      Shell to execute rather than $SHELL.
-S sockname   Name this session <pid>.sockname instead of <pid>.<tty>.<host>.
-t title      Set title. (window's name).
-T term       Use term as $TERM for windows, rather than "screen".
-U            Tell screen to use UTF-8 encoding.
-v            Print "Screen version 4.03.01 (GNU) 28-Jun-15".
-wipe [match] Do nothing, just clean up SockDir [on possible matches].
-x            Attach to a not detached screen. (Multi display mode).
-X            Execute <cmd> as a screen command in the specified session.
```


