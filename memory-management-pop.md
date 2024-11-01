# To get a list of memory usage:
```
ps -eo size,pid,user,command --sort -size | \
    awk '{ hr=$1/1024 ; printf("%13.2f Mb ",hr) } { for ( x=4 ; x<=NF ; x++ ) { printf("%s ",$x) } print "" }' |\
    cut -d "" -f2 | cut -d "-" -f1 > test.txt

```

# Recommended things to free up ~1gb+ of ram 
- Stop docker when not running
- Close out node/go servers when done
- stop the dumb app store from having on startup (this uses 800mb) 
```
cd /etc/xdg/autostart/
mv io.elementary.appcenter-daemon.desktop io.elementary.appcenter-daemon.desktop.bak 
```
