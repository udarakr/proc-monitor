## Process analysis bash script

*Purpose of this tool is to analyze process log files created by the previous script*

- Create analyze.sh with the following content and provide execute permission with chmod +x analyze.sh

```
#!/bin/sh
rm analyze
for filename in ~/proc_log/top.*; do
    printf '%*s\n' "${COLUMNS:-$(tput cols)}" '' | tr ' ' - >> analyze
    printf '%*s\n' "${COLUMNS:-$(tput cols)}" '' | tr ' ' - >> analyze
    printf "%s\n" "$filename" >> analyze
    head -n 1 $filename >> analyze
    sort -k4 -n -r $filename | head -n 10 >> analyze   
    printf '%*s\n' "${COLUMNS:-$(tput cols)}" '' | tr ' ' - >> analyze
    sort -k3 -n -r $filename | head -n 10 >> analyze   
done
```
