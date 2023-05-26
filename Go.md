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

#### Go Get

- `go get -u ./...` walks all packages in your project. **This is the command you want to use.**
- `go get -t -u ./...` walks all packages in your project and also downloads tests files of these dependencies. Probably you don’t need that.
- `go get -u` updates in the current directory only. Useful for small single-package projects, just use the first version.
- `go get -u specific.com/package` updates just one (or more separated by space) packages (and dependencies).
- `go get -u specific.com/package@version` the same but to a specific version.
- `go get -u all` updates modules from the [build list](https://go.dev/ref/mod#glos-build-list) from `go.mod`. This is useful for listing (`go list -m -u all`) but not too useful for updates.



#### Go Mod

###### Go 1.16 requires use of Go modules by default, to still allow working as before

```
#export GO111MODULE=off
#export GO111MODULE=auto
export GO111MODULE=on
#export GOFLAGS=-mod=readonly
export GOFLAGS=-mod=mod
#export GOFLAGS=-mod=vendor
#export GOPROXY=on
export GOPROXY=direct
#export GOPROXY=off
#To fix error:0308010C:digital envelope routines::unsupported
export NODE_OPTIONS=--openssl-legacy-provider

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
go get -u all
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

