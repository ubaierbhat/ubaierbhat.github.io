---
layout: post
title: "python hack to share current directory"
date: 2019-12-08
---

# python hack to share current directory with others on lan
```bash
alias quickshare="python3 -m http.server"
```
The directory will be shared on `http://{lanip}:8000`

Make sure your kill the server once you are done. 

_Note: This won't work if your current directory has an index.html file._