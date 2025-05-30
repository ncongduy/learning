## Contents

- find a file which has the highest number of line
```bash
find . -type f -exec wc -l {} \; | sort -nr | head -n 1
```
