Run Node-RED Sample Script
------


```
#!/bin/bash
scriptPath=$(realpath ${BASH_SOURCE[0]})
scriptDir=$(dirname ${scriptPath})
#printf " %s\n" $(printf "=%.0s" {1..83}|sed -e 's/=/-/g')
#printf "| %-30s| %-50s|\n" "Name" "Value"
#printf "| %s |\n" $(printf "=%.0s" {1..81})
#printf "| %-30s| %-50s|\n" "scriptDir" $scriptDir
#printf "| %s |\n" $(printf "=%.0s" {1..81}|sed -e 's/=/-/g')
#printf "| %-30s| %-50s|\n" "scriptPath" $scriptPath
#printf " %s\n" $(printf "=%.0s" {1..83}|sed -e 's/=/-/g')
PIDFILE=/var/run/node-red/test.pid
mkdir -p /var/run/node-red
start(){
  start-stop-daemon \
    --start \
    --quiet \
    --make-pidfile \
    --pidfile $PIDFILE \
    --background \
    --exec $(which node-red) -- \
    -s $scriptDir/node-red-settings.js -u $scriptDir && echo $?
}
stop(){
  start-stop-daemon --stop --quiet --pidfile $PIDFILE && echo $?
}
help(){
cat << EOF
Usage:
  $0 start|stop
EOF
}
[ -z "$1" ] && help
case "$1" in
  start)
    $1
    ;;
  stop)
    $1
    ;;
  restart)
    stop
    start
    ;;
  *)
    ;;
esac

```
