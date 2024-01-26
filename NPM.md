# NPM

build

```
# build for test environment
npm run build:stage

# build for production environment
npm run build:prod
```



```
# preview the release environment effect
npm run preview

# preview the release environment effect + static resource analysis
npm run preview -- --report

# code format check
npm run lint

# code format check and auto fix
npm run lint -- --fix
```





npm install npm@latest -g

npm config set prefer-offline true
  npm --cache-min 9999999 install <package-name>

.npmrc



##### Set a new registry for a scoped package
@myscope:registry=https://localhost:8080/repository/node_modules




rsync -R -avz -e ssh --rsync-path="echo mypassword | sudo -S  mkdir -p /remote/folder && sudo rsync" /home/ubuntu/my/folder ubuntu@x.x.x.x:/remote/folder --delete

