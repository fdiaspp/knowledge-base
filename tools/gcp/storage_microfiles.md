# Cloud Storage - Handling Microfiles



# `gsutils compose` Strategy
This commands has certains limitations. But it's possible to overcome those applying an interate resolution. As discussed on stack overflow thread mentione below, the strategy aims to do somenthing like, where in a bucket we have files a, b and c:

```
file_d = compose(file_a, file_b)
remove(file_a, file_b)
filed = compose(file_d, file_c)
remove(file_c)
```

Source:
https://stackoverflow.com/questions/20876780/how-to-append-write-to-google-cloud-storage-file-from-app-engine

