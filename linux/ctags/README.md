
##### Install ctags on Ubuntu:    
>     
> ```
> apt-get install exuberant-ctags
> ```
> 
##### Usage examples: 
>
> ``` 
> ctags -R
> ```
> 
> With file list: 
> ```
> ctags -L <source code list>
> ```
##### Language map: 
> 
> ```
> ctags -R --langmap=C++:+.ino --verbose `pwd`
> ```
> 
