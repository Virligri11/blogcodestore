---
title: deploy with netlify
date: 2024-05-24 15:30:15
tags: Coding
describtion: problem that meet when deploy on netlify. About the "submodules"
---

To making the submodules work need to remove all the `.git` files in the site that git can not detect the use of submodules of other model.


First
```
# Remove the submodule entry from .git/config
git submodule deinit -f path/to/submodule

# Remove the submodule directory from the superproject's .git/modules directory
rm -rf .git/modules/path/to/submodule

# Remove the entry in .gitmodules and remove the submodule directory located at path/to/submodule
git rm -f path/to/submodule
```

If the file still exist. I suggest that moving the file to other folder then delete the `.git` file and add it to thethemes again.
