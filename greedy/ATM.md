백준 ATM 실버3
시간이 짧은걸 먼저 처리해주면 되는 문제 
```python
n=int(input())
p=list(map(int, input().split()))
p.sort()
answer=0
dap=0
for i in p:
    answer=answer+i
    dap+=answer
print(dap)
```
