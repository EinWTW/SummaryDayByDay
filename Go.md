# Go

#### GO ENV
```
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```


#### Go 1.16 requires use of Go modules by default, to still allow working as before
```
#export GO111MODULE=off
export GO111MODULE=on
#export GOFLAGS=-mod=readonly
export GOFLAGS=-mod=mod
#export GOFLAGS=-mod=vendor
```



###### update go.mod

```
go mod tidy
```



###### replace go module path

```golang
go mod edit -replace="github.com/relab/hotstuff@v0.2.2=github.com/EinWTW/hotstuff@v0.2.2"
```

###### 

###### go get branch

```
go get github.com/EinWTW/hotstuff@veritashs-experiment
```



###### delete go package

```
go get package@none
```





