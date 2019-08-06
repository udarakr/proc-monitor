## Process monitoring bash script

*Purpose of this tool is to register a cronjob which will periodically log existing processes*

- Create regcron.sh with the following content and provide execute permission with chmod +x regcron.sh

```
#!/bin/sh

mkdir ~/proc_log
tmp=''
echo '*/5 * * * * cd ~/proc_log && ps -aux > "top.`date +\%Y\%m\%d-\%H:\%M:\%S`"' > '$tmp'
crontab < '$tmp'
```

- run ./regcron.sh to create process log directory and install the cronjob.

- Once we are done with the analysis(enough process log files) create unregcron.sh with the following and provide execute permission with chmod +x unregcron.sh

- Take a backup of the proc_log directory.

```
 #!/bin/sh

rm -r  ~/proc_log
crontab -r
```

- run ./unregcron.sh to remove process log directory and remove the cronjob.
