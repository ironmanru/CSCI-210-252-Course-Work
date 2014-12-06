###Lab 5 Timesheet
```
#!/bin/bash
# ts_input
# sassenbergm
echo $TD
echo -n $TD " ">>$HOME/public_html/timesheet.log

dialog --inputbox "Enter your name:" 8 40 2>>$HOME/public_html/timesheet.log
echo -n "| ">>$HOME/public_html/timesheet.log
clear

echo "Enter project name and description:"
read INPVAR
echo $INPVAR >>$HOME/public_html/timesheet.log
#Add to log file

#Add to HTML file
$HOME/public_html/ts_mkweb

echo "Done."

--------------------------

#!/bin/bash
# ts_mkweb
# sassenbergm
echo $HDR > $HOME/public_html/timesheet.html
cat $HOME/public_html/timesheet.log >> $HOME/public_html/timesheet.html
echo $FTR >> $HOME/public_html/timesheet.html
#eof

-------------------------
#!/HOME/.bashrc
# bashrc
# sassenbergm

test -s ~/.funcs && . ~/.funcs || true

export HDR="<html><head><title>Timesheet</title></head><body><pre>"
export FTR="</pre></body></html>"
```


