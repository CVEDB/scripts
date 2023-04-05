### add-dot-at-end
<img src="https://img.shields.io/badge/language-bash-black">
Add . at the end of each line in files.
```
find in -type f -exec cat {} + | sed 's/$/./' | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### add-line-to-shodan-query
<img src="https://img.shields.io/badge/language-bash-black">
Add lines to values of shodan query.
```
find in -type f -exec cat {} + | awk '{ if ($0 != "") print "ssl.cert.subject.cn:\"*."$0"\""}'  | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### append-headers-to-csv
<img src="https://img.shields.io/badge/language-bash-black">
Append headers supplied to csv file without them.
```
(echo "vulnerability_id,tags,description,authors,severity,type,host,ip,match,vuln_name,extracted_results,timestamp" && find in -type f -exec cat {} +) > out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### awk-print-last-column
<img src="https://img.shields.io/badge/language-bash-black">
Prints last column of a files in in folder.
```
find in -type f -exec cat {} +  | awk '{print $(NF)}' | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### awk-take-first-row
<img src="https://img.shields.io/badge/language-bash-black">
Extract first column from all files in in directory.
```
find in -type f -exec cat {} + | awk -F " " '{print $1}' | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### awk-take-second-row
<img src="https://img.shields.io/badge/language-bash-black">
Extract second column from all files in in directory.
```
find in -type f -exec cat {} + | awk -F " " '{print $2}' | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
