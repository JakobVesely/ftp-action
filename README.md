# FTP Action Delete & Upload
Based on [sebastianpopp/ftp-action](https://github.com/sebastianpopp/ftp-action).
Exactly the same Github Action with the addition of **lftp** mirror options **--Remove-source-files** and **--Remove-source-dirs**!

See the lftp manual: http://lftp.yar.ru/lftp-man.html

## Example usage

```
name: Deploy via ftp
on: push
jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Upload ftp
      uses: sebastianpopp/ftp-action@releases/v2
      with:
        host: ${{ secrets.FTP_SERVER }}
        user: ${{ secrets.FTP_USERNAME }}
        password: ${{ secrets.FTP_PASSWORD }}
        localDir: "dist"
        remoteDir: "www"
```

## Input parameters

Input parameter | Description | Required | Default
--- | --- | --- | ---
host | FTP server name | Yes | N/A
user | FTP username | Yes | N/A
password | FTP password | Yes | N/A
localDir | The local directory to copy | No | .
remoteDir | The remote directory to copy to | No | .
forceSsl | Force SSL encryption | No | false
