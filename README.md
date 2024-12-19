# Linux_Tips_and_Tricks
some tips to work with linux or find problem
# test Performance od disk
```
dd if=/dev/random of=./test bs=1M count=200
```
output is like this : <br>
![disk](https://github.com/user-attachments/assets/fae38e13-0728-46f1-ad2f-99cc79f79ee4) <br>
and then agian : <br>

```
dd if=/dev/random of=./test bs=2M count=100
```
