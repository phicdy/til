# -e option

If -e option is set, bash finished the script immediately if return code is non-zero.

```bash
#!/bin/bash -e
false
echo "hoge" # Not executed
```
"set -e" also set the option

```bash
#!/bin/bash
false
echo "executed"
set -e
false 
echo "Not executed"
```

"set +e" disable the option.

```bash
#!/bin/bash -e
set +e
false 
echo "executed"
```
