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

`Ctrl + a`, then `n` or `p` to go to next or previous window. 


