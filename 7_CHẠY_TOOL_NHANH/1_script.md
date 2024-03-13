# SCRIPT CHẠY TOOL NHANH HƠN.




```
#!/bin/bash

SCRIPT="a.sh"

./SCRIPT


nice -n -20 bash SCRIPT

PID=$(pgrep -f $SCRIPT)

ulimit -l 8000 -p PID












```



