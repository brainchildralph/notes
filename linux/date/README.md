
Busybox Date
------

```
# Format Test
date -D %Y%m%d%H%M -d 201607131001 +'%I:%M %p %B %d, %Y'

#
export TZ=CST-8
date
unset TZ
date

```



```
date +FORMAT //定製時間顯示格式
date '+%Y/%m/%d %H:%M:%S'

Weekday:
    %a   locale's abbreviated weekday name (e.g., Sun)
    %A   locale's full weekday name (e.g., Sunday)
    %U   week number of year, with Sunday as first day of week (00..53)
    %W   week number of year, with Monday as first day of week (00..53)
    %V   ISO week number, with Monday as first day of week (01..53) //start from Monday strictly!
Year:
    %Y   year(1970-2038(32bit))
    %y   last two digits of year (00..99)
    %g   last two digits of year of ISO week number (see %G) //date --date '2013-12-29' +%V+%A+%g+%G
    %G   year of ISO week number (see %V); normally useful only with %V //date --date '2013-12-30' +%V+%A+%g+%G
Month:
    %m   month (01..12)
    %b   locale's abbreviated month name (e.g., Jan)
    %B   locale's full month name (e.g., January)
    %h   same as %b
Day:
    %d   day of month (e.g., 01)
    %e   day of month, space padded; same as %_d
    %u   day of week (1..7); 1 is Monday
    %w   day of week (0..6); 0 is Sunday
    %j   day of year (001..366)
Hour:
    %H   hour (00..23)
    %I   hour (01..12)
    %k   hour, space padded ( 0..23); same as %_H
    %l   hour, space padded ( 1..12); same as %_I
    %p   locale's equivalent of either AM or PM; blank if not known
    %P   like %p, but lower case
Minute:
    %M   minute (00..59)
Seconds:
    %S   second (00..60)
Timestamp:
    %s   seconds since 1970-01-01 00:00:00 UTC
Comlpex:
    Full date&time:
        %c   locale's date and time (e.g., Thu Mar  3 23:05:25 2005)
    Full date:
        %x   locale's date representation (e.g., 12/31/99)
        %D   date; same as %m/%d/%y
        %F   full date; same as %Y-%m-%d
    Full time:
        %X   locale's time representation (e.g., 23:13:48)
        %T   time; same as %H:%M:%S
        %r   locale's 12-hour clock time (e.g., 11:11:04 PM)
        %R   24-hour hour and minute; same as %H:%M

Century:
    %C   century; like %Y, except omit last two digits (e.g., 20)
Other:
    %n   a newline
    %N   nanoseconds (000000000..999999999)
    %t   a tab
    %z   +hhmm numeric time zone (e.g., -0400)
    %Z   alphabetic time zone abbreviation (e.g., EDT)
```
