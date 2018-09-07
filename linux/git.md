# Git

## scripts

### filter branch
```
git filter-branch --env-filter '
NEW_NAME=""
NEW_EMAIL=""

if [[ "$GIT_COMMITTER_NAME" =~ XXX ]]; then
    export GIT_COMMITTER_NAME="$NEW_NAME"
    export GIT_COMMITTER_EMAIL="$NEW_EMAIL"
fi
if [[ "$GIT_AUTHOR_NAME" =~ XXX ]]; then
    export GIT_AUTHOR_NAME="$NEW_NAME"
    export GIT_AUTHOR_EMAIL="$NEW_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```

### Remove original refs
```
git for-each-ref --format="%(refname)" refs/original/ | xargs -n 1 git update-ref -d
```
