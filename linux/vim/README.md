
##### CSCOPE vim config

```
set csprg=/usr/bin/cscope               "cscope位置
set csto=0                                              "cscope DB search first
set cst                                                 "cscope DB tag DB search
set nocsverb                                    "verbose off
cs add /home/xxx/linux-3.5/cscope.out   /home/xxx/linux-3.5
if filereadable("cscope.out")
  cs add cscope.out
elseif $CSCOPE_DB != ""
  cs add $CSCOPE_DB
endif
```

