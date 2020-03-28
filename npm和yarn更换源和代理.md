## npm和yarn转换淘宝源和官方源
```
  npm config set registry http://registry.npm.taobao.org/
  npm config set registry https://registry.npmjs.org/

  yarn config set registry http://registry.npm.taobao.org/
  yarn config set registry https://registry.npmjs.org/
```

## npm 设置代理
```
  npm config set proxy http://127.0.0.1:1080
  npm config set https-proxy http://127.0.0.1:1080
```
## npm 删除代理
```
  npm config delete proxy
  npm config delete https-proxy
```

## yarn 设置代理
```
  yarn config set proxy http://127.0.0.1:1080
  yarn config set https-proxy http://127.0.0.1:1080
```
## yarn 删除代理
```
  yarn config delete proxy
  yarn config delete https-proxy
```

## git 设置代理
```
  git config --global https.proxy http://127.0.0.1:1080

  git config --global https.proxy https://127.0.0.1:1080

  git config --global --unset http.proxy

  git config --global --unset https.proxy
```