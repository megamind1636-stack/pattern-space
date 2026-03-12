Example file:

```
apple
banana
cat
dog
```

### Case 1 — `sed 'p' file.txt` (default printing ON)

```
Cycle 1
Input line: apple
Pattern Space: [ apple ]

p command prints → apple
Default sed print → apple

Output so far:
apple
apple
```

```
Cycle 2
Input line: banana
Pattern Space: [ banana ]

p command prints → banana
Default sed print → banana

Output so far:
apple
apple
banana
banana
```

```
Cycle 3
Input line: cat
Pattern Space: [ cat ]

p command prints → cat
Default sed print → cat
```

```
Cycle 4
Input line: dog
Pattern Space: [ dog ]

p command prints → dog
Default sed print → dog
```

Final output:

```
apple
apple
banana
banana
cat
cat
dog
dog
```

Reason:
`p` printed once + sed automatically printed again.

---

# Case 2 — `sed -n 'p' file.txt` (default printing OFF)

`-n` disables automatic printing.

```
Cycle 1
Input line: apple
Pattern Space: [ apple ]

p command prints → apple
(no automatic print)
```

```
Cycle 2
Input line: banana
Pattern Space: [ banana ]

p command prints → banana
```

```
Cycle 3
Input line: cat
Pattern Space: [ cat ]

p command prints → cat
```

```
Cycle 4
Input line: dog
Pattern Space: [ dog ]

p command prints → dog
```

Final output:

```
apple
banana
cat
dog
```

---

# Case 3 — Real usage (`sed -n '2p' file.txt`)

```
Cycle 1
Line: apple
Pattern Space: [ apple ]
(no p command triggered)
Output: nothing
```

```
Cycle 2
Line: banana
Pattern Space: [ banana ]
2p triggers → print banana
```

```
Cycle 3
Line: cat
Pattern Space: [ cat ]
no print
```

```
Cycle 4
Line: dog
Pattern Space: [ dog ]
no print
```

Output:

```
banana
```

---

# Mental model

```
Without -n

Input → Pattern Space → Commands → Print automatically


With -n

Input → Pattern Space → Commands → Print ONLY if 'p'
```

---

Important sed intuition:

```
sed = stream editor

Line enters
↓
Pattern space
↓
Commands run
↓
Print
↓
Pattern space cleared
↓
Next line
```
