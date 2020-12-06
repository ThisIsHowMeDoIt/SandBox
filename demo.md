---
---
[[HOME](index.md)] [[GitHub](https://github.com/ThisIsHowMeDoIt/SandBox/)]

# Source Codes

<br>
## File "index.md"
```
---
---

# This Is How Me Do It!

| [![This Is How Me Do It](https://img.youtube.com/vi/PVi8bJFIac8/0.jpg)](https://www.youtube.com/watch?v=PVi8bJFIac8) |

* [Source Code](demo.md)

```

<br>
## File "Makefile"
```
# Sun 06 Dec 2020 22:11:04 WIB

demo.md: demo.pmd
	python .program/includeScript.py < demo.pmd > demo.md

```

<br>
## Script File "script.sh"
```
#!/bin/bash

ls -al

```

<br>
## Python Source Code "includeScript.py"
```
# (c) 2011 Brice Fernandes. This script was ripped from 
# https://fractallambda.com/2011/08/17/pincpy-including-files-and-script-output.html
# Note: This script is outdated.  
# The author uses Handlebars.js or Pystache for the same purpose.
# Usage: 
#     python .program/xx.py < in.pmd > out.md

import sys
import re
import shlex
import subprocess as sp
 
exe_pat = re.compile(r'(\s*)\(!>(.*)<\)\s*')
inc_pat = re.compile(r'(\s*)\(>(.*)<\)\s*')
 
if __name__ == "__main__":
  for line in sys.stdin:
    match_exe = re.match(exe_pat, line)
    match_inc = re.match(inc_pat, line)

    if match_exe:
      space = match_exe.group(1)
      exe = match_exe.group(2).strip()
      args = shlex.split(exe)
      sys.stdout.writelines(
        map(
          lambda x: space+x+"\n", 
          sp.check_output(args).split("\n")))

    elif match_inc:
      space = match_inc.group(1)
      inc = match_inc.group(2).strip()
      sys.stdout.writelines(
        map(
          lambda x: space+x, 
          open(inc)))

    else:
      sys.stdout.write(line)

```

<br>
## This Demo File
```
---
---
[[HOME](index.md)] [[GitHub](https://github.com/ThisIsHowMeDoIt/SandBox/)]

# Source Codes

<br>
## File "index.md"
```
(> index.md <)
```

<br>
## File "Makefile"
```
(> Makefile <)
```

<br>
## Script File "script.sh"
```
(> scripts/script.sh <)
```

<br>
## Python Source Code "includeScript.py"
```
(> .program/includeScript.py <)
```

<br>
## This Demo File
```
(> demo.pmd <)
```

<br>
# Jolan Tru!

```

<br>
# Jolan Tru!

