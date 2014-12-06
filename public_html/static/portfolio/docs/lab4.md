###Lab 4 Script 1

```
#!/bin/bash
# script!
# lab 4 script1
# sassenbergm
clear
echo -n "Enter your first name: "
read NAME1 
echo -n "Enter your first number: "
read NUM1
echo -n "Enter your second number: "
read NUM2
SUM1=$((NUM1+NUM2))

echo "Hello $NAME1, the sum of the two numbers is: $SUM1"
echo $(date +%s) $NAME1 $SUM1 >> $HOME/public_html/script1.log
```
