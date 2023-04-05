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
### awk-take-third-row
<img src="https://img.shields.io/badge/language-bash-black">
Extract third column from all files in in directory.
```
find in -type f -exec cat {} + | awk -F " " '{print $3}' | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### cat-from-to-lines
<img src="https://img.shields.io/badge/language-bash-black">
Cat file from line number to line number with sed.
```
sed -n 1,100p in/*/* | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### clone-github-repository
<img src="https://img.shields.io/badge/language-bash-black">
Efficiently clone a GitHub repository using the appropriate configuration.
```
USERNAME="YOUR_GITHUB_USERNAME"
EMAIL="YOUR_GITHUB_EMAIL"
REPOSITORY="USER/REPO"
TOKEN=$(cat /hive/in/http-input-1/output.txt)

BRANCH="main"

git config --global user.email "$EMAIL"
git config --global user.name "$USERNAME"
git config --global pack.windowMemory "50m"
git config --global http.version HTTP/1.1
git config --global http.postBuffer 157286400
git config --global http.lowSpeedLimit 0
git config --global http.lowSpeedTime 999999

git clone -b $BRANCH --depth 1 https://$USERNAME:$TOKEN@github.com/$REPOSITORY.git
cd $(echo $REPOSITORY | awk -F '/' '{print $2}')

# process your repository here
ls | tee /hive/out/output.txt

```
Contributed by [cvedb](https://cvedb.github.io)
---
### convert-piped-ip-ports
<img src="https://img.shields.io/badge/language-bash-black">
Converts output with | delimiter to ip:port format.
```
find in -type f -exec cat {} + | awk -F"|" '{print $1":"$2}' | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### count-lines-in-all-files
<img src="https://img.shields.io/badge/language-bash-black">
Used to quickly count all lines inside of all files in in folder.
```
find in -type f -exec cat {} + | wc -l | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### create-wordlist-from-robots-txt
<img src="https://img.shields.io/badge/language-bash-black">
One-liner for generating wordlists from robots.txt
```
find in/ -mindepth 3 -type f -exec cat {} + | egrep -w "Disallow|Allow: " | awk '{print $2}' | sed 's/^\///' | sed 's/\/$//' | sed '/^[[:space:]]*$/d'| sed 's/\*$//' | sed 's/^\*//' | sed 's/\/$//' | sed -e 's/\*\///g' | sed -e s/\*//g | uniq | tee out/output.txt
```
Contributed by [kljunowsky](https://cvedb.github.io)
---
### delete-dot-as-first-char
<img src="https://img.shields.io/badge/language-bash-black">
Delete dot when first character, usefull for parsing subdomains with not valid results.
```
cat in/*/* | sed 's/^\.//' | sort -n | uniq | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### delete-dot-as-last-char
<img src="https://img.shields.io/badge/language-bash-black">
Delete dot when it is last character, massdns anyone?
```
cat in/*/* | sed 's/\.$//' | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### egrep-multiple-values
<img src="https://img.shields.io/badge/language-bash-black">
Egrep multiple values and print last in array.
```
cat in/*/* | egrep -w 'url|robots|linkfinder' | awk -F" " '{print $NF}' | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### egrep-urls-from-list-of-files
<img src="https://img.shields.io/badge/language-bash-black">
Extract urls from list of files with regex.
```
find in -type f -exec cat {} + | egrep -o 'https?://[^ ]+' | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### eof-raw-data
<img src="https://img.shields.io/badge/language-bash-black">
Paste raw data and add it to output.
```
cat << "EOF" | tee out/output.txt
ADD_CONTENT_HERE
EOF

```
Contributed by [cvedb](https://cvedb.github.io)
---
### extract-ips-with-regex
<img src="https://img.shields.io/badge/language-bash-black">
Extract ip addresses from files with regex.
```
find in -type f -exec cat {} + | grep -E -o "(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)" | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### find-strings-in-meg-responses
<img src="https://img.shields.io/badge/language-bash-black">
Find string in meg responses and print urls.
```
for f in $(find in -mindepth 3 -type f -exec grep 'root:' -R {} + | cut -d":" -f1 | sort -u); do echo "$(head -1 $f) [VULNERABLE]" | egrep '^http'; done | tee out/output.txt
```
Contributed by [gliga](https://cvedb.github.io)
---
### generate-random-passwords
<img src="https://img.shields.io/badge/language-bash-black">
Utility to generate random passwords based on pwgen.
```
pwgen -N 100 5 | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
### generate-sequence-of-numbers
<img src="https://img.shields.io/badge/language-bash-black">
Sequence of numbers generator!
```
for i in {1..10};do echo $i;done | tee out/output.txt
```
Contributed by [cvedb](https://cvedb.github.io)
---
