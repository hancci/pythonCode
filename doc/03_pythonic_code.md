## startswith
```python
with open('./3.txt') as f:
    for line in f:
        if line.startswith(('APPO','SVC')):
            print(line.strip('\n\r'))
```