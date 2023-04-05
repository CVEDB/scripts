### add-dot-at-end
<img src="https://img.shields.io/badge/language-bash-black">
Add . at the end of each line in files.
```
find in -type f -exec cat {} + | sed 's/$/./' | tee out/output.txt
```
Contributed by [trickest](https://cvedb.github.io)
---
