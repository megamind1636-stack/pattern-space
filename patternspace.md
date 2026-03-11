Bhai, bahut simple hai. Aise samajh:

**Sed kaise kaam karta hai:**

Soch le teri file mein 5 lines hain. Sed **ek ek line** uthata hai aur process karta hai.

```
File:
Line 1: hello   world
Line 2: foo     bar
Line 3: bye     all
```

**Pattern Space = Sed ka workspace/workbench**

Jaise tu koi cheez repair karta hai toh table pe rakhta hai na? Wahi hai pattern space. Sed ek line uthata hai → pattern space mein rakhta hai → uspe command lagata hai → output de deta hai → phir agla line uthata hai.

```
Step 1: "hello   world" → pattern space mein aaya
        sed command lagao (e.g., extra spaces hatao)
        result: "hello world" → print karo
        pattern space khali karo

Step 2: "foo     bar" → pattern space mein aaya
        sed command lagao
        result: "foo bar" → print karo
        pattern space khali karo

... aur aise hi aage
```

**Ab `sed -n` kya karta hai?**

Normally sed har line process karke **automatically print** kar deta hai. `-n` bolta hai — "auto print mat kar, main khud bataunga kab print karna hai."

```bash
# Bina -n: sab lines print hogi
sed 's/hello/hi/' file.txt

# -n ke saath: kuch print nahi hoga (kyunki auto-print band hai)
sed -n 's/hello/hi/' file.txt

# -n + p flag: sirf wahi line print hogi jahan match hua
sed -n 's/hello/hi/p' file.txt
```

**Real example:**

```bash
# File mein se sirf 3rd line dikhao
sed -n '3p' file.txt

# Sirf woh lines dikhao jismein "error" ho
sed -n '/error/p' file.txt
```

Toh basically — **pattern space = sed ka temporary kaam karne ka jagah**, aur **`-n` = auto print band kar, sirf jab `p` bolu tab print kar**.
