# Go

#### GO ENV
```
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```

Install

```
curl -OL https://golang.org/dl/go1.16.15.linux-amd64.tar.gz
tar -xvf ./go1.16.15.linux-amd64.tar.gz

#export GOROOT=$HOME/local/go
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

###### list sub packages

If you want to see *all* sub-packages under a specific package you can use `go list` command:

```golang
go list crypto/...
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

###### go get all package

```

```



###### delete go package

```
go get package@none
```

###### go doc

```golang
godoc -http=:6060

*open your browser and visit localhost:6060*
```

Usage:

```golang
go get [-d] [-f] [-t] [-u] [-v] [-fix] [-insecure] [build flags] [packages]
```

Get downloads the packages named by the import paths, along with their dependencies. It then installs the named packages, like 'go install'.

The -d flag instructs get to stop after downloading the packages; that is, it instructs get not to install the packages.

The -f flag, valid only when -u is set, forces get -u not to verify that each package has been checked out from the source control repository implied by its import path. This can be useful if the source is a local fork of the original.

The -fix flag instructs get to run the fix tool on the downloaded packages before resolving dependencies or building the code.

The -insecure flag permits fetching from repositories and resolving custom domains using insecure schemes such as HTTP. Use with caution.

The -t flag instructs get to also download the packages required to build the tests for the specified packages.

The -u flag instructs get to use the network to update the named packages and their dependencies. By default, get uses the network to check out missing packages but does not use it to look for updates to existing packages.

The -v flag enables verbose progress and debug output.

