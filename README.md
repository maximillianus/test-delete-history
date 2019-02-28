# test-delete-history
test delete history

## How to delete history once you push in sensitive data?
[Reference](https://help.github.com/en/articles/removing-sensitive-data-from-a-repository)
- git clone `YOUR_REPOSITORY`
- cd `YOUR_REPOSITORY`
- copy your `FILE_WITH_SENSITIVE_DATA` 
  - `cp sensitive.txt not_so_sensitive.txt`
- delete your `FILE_WITH_SENSITIVE_DATA` 
  ```
  git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch ./to_delete.py' --prune-empty --tag-name-filter cat -- --all
  ```
- add `COPIED_FILE_WITH_LESS_SENSITIVE_DATA` to git
  - `git add not_so_sensitive.txt`
- `git commit -m 'pushing safe file'`
- *to ensure, you can add filename with sensitive data to .gitignore*
  - `echo "sensitive.txt" >> .gitignore`
- `git push origin --force --all`
