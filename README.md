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
