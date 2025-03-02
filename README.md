# Linux_Tips_and_Tricks
some tips to work with linux or find problem
# test Performance on disk
```
dd if=/dev/random of=./test bs=1M count=200
```
output is like this : <br>
![disk](https://github.com/user-attachments/assets/fae38e13-0728-46f1-ad2f-99cc79f79ee4) <br>
and then agian : <br>

```
dd if=/dev/random of=./test bs=2M count=100
```
![disk2](https://github.com/user-attachments/assets/c1e0ce5b-a3d4-406b-81ef-dc1f36e1d805) <br>

note : if we increase the bs --> we increase the thouput <br>
note : if we increase the count --> we increase the IOPS

tools for checking iops :
```
apt install sysstat
service sysstat restart 
```
now use sar command : <br>

- check kernel version : <br>
```
uname -a
```
- check os version : <br>
```
cat /etc/lsb-release
```
- check uptime and load average : <br>
```
uptime
```
 - check cpu count if load average was high : <br>
 ```
cat /proc/cpuinfo
```
- check memory info : <br>
```
cat /proc/meminfo
```
- check total load : <br>
```
top
```
- check system with sar : (1 is interval )(10 is count of excueting command )(b is block )(d is disk )(n is network )<br> 
```
sar -b -d 1 10
sar -n TCP 1
```
- check network port used : <br>
```
ss -ltnp
ss -lunp
```
- check tcpdump : <br>
```
tcpdump -i ens192 host 192.168.1.100 and port 22
tcpdump -i ens192 host 192.168.1.100 and port not 22
```
- check io
```
apt install iotop
```
- check proccesses: <br>
```
ps -aux
```
- kill proccess : <br>
```
kill -9 PID
```
# Ocuupied Disk Space : <br>
```
df
df -h
cd / (Ocuupied directory)
du -sh .
```
find occupied directory . with du -sh . <br>
find large files in that directory <br>
try to find which proccess do that file extermeley large ? <br>
try to do not delete files directrly . because maybe some proccess writing on taht files and deleting that files caused error . and now you do not have lg file .after that you should reset your service . <br>
do not use cat  pipe on big files.  <br>
find large files and try to find proccess of maker . <br>
```
ps -aux | grep file.log | grep -v grep
while true; do ps aux | grep file.log | grep -v grep; done
lsof file.log
while true; do lsof file.log ; done
```
we can rm file and then check lsof agian .somtime if disk is fully occupied , that unkhown proccess cant write on the file. while disk is free , <br> proccess start to write and can lsof <br>
```
while true; do ps aux | grep file.log | grep -E -v "watch|grep"; done
```
with up command , we can find command that occupied disk . (for example that command is head)

we can find extra large file with gig size with this command : <br>
```
du -h <dir> 2>/dev/null | grep '[0-9\.]\+G'
```
```
while true; do ps auxf | grep head | grep -v grep; done
while true; do ps auxf | grep -B5 head | grep -v grep; done
```
now we can find script to occupied disk space . <br>

in this case , we find a proccess . sometimes maybe would be a crucial service that we can not delete . so maybe decrese log level <br>
can help us . 



