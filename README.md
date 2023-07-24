Based on [`Azure Storage Action`](https://github.com/lauchacarro/Azure-Storage-Action)


### Sample workflow
```

on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps: 
    - uses: actions/checkout@v1
    - uses: actions/setup-dotnet@v1
      with:
        dotnet-version: '3.0.100'
    - uses: lauchacarro/Azure-Storage-Action@master
      with:
        enabled-static-website: 'true'
        folder: 'MyFolder'
        index-document: 'index.html'
        error-document: '404.html' # For Angular apps with routing enabled, this must point to the index.html file because the requested routes don't exist phyiscally and blob storage would throw a 404.
        connection-string: ${{ secrets.CONNECTION_STRING }}

```
Accepts index-document & error-document as workflow inputs
