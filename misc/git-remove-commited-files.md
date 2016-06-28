[github](https://help.github.com/articles/remove-sensitive-data/)
git filter-branch --force --index-filter 'git rm --cached --ignore-unmatch config.py' --prune-empty --tag-name-filter cat -- --all
