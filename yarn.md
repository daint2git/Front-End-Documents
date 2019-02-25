Update tất cả các modules trong package.json lên phiên bản mới nhất
```
$ git reset --hard
// undo changes to yarn.lock
$ yarn upgrade --latest
// this time, package.json gets updated.
