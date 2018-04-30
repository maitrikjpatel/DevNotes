
# GIT Notes

---

## Git Help

- [Github Page](https://help.github.com/articles/create-a-repo)
- [Set Up Git](https://help.github.com/articles/set-up-git)
- [Understanding Git Flow](https://guides.github.com/introduction/flow/index.html)
- [GITHUB Cheat Sheet](https://github.com/tiimgreen/github-cheat-sheet)
- [Flight rule for GIT](https://github.com/k88hudson/git-flight-rules)


## [GIT Submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules)**

**Adding a Submodule to a Repository**
```
git submodule add <url> <destination>
```

**Submodule Basic commands**
```
git submodule status
git submodule init
git submodule update
```

**Update Submodule URLs**
```
git submodule sync
```

### Remove a submodule

```
git submodule deinit <submodule location>
git rm -rf <submodule location>
```

**Clone submodule in a cloned repository**
```
git submodule update --remote
git submodule update --init --recursive
```

### Update all submodules
```
git submodule foreach git pull origin master
cd ..
git commit . -m "Updated submodules"
git push
```

### Edit a submodule
```
cd components/canvasrunner
<edit>
git commit . -m "Edited"
git push
cd ...
git commit . -m "bumped canvasrunner"
git push
```

### Clone repositories with submodules
```
git clone --recursive
```

### Pull submodule if you forgot to clone --recursive
```
cd components/canvasrunner
git submodule update --init
```

---
##Author

- Maitrik Patel || maitrikpatel.com || maitrik1419[at]gmail[dot]com
