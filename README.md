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
```

