# About Go modules

A module is a collection of related Go packages that are versioned together as a single unit.
Modules record precise dependency requirements and create reproducible builds.

Summarizing the relationship between repositories, modules, and packages:

* A repository contains one or more Go modules.
* Each module contains one or more Go packages.
* Each package consists of one or more Go source files in a single directory.

If you add a new import to your source code that is not yet covered by a require in go.mod, most go commands like 'go build' and 'go test' will automatically look up the proper module and add the highest version of that new direct dependency to your module's go.mod as a require directive.

## Initialize a new Go module

You need to execute this command outside GOPATH!

```
$ go mod init github.com/scraly/myproject
```

This command create the initial module definition and write it to the go.mod file.

## Migrate from existing dependency manager (dep, glide, govendor, godep ...) to go modules

```
$ go mod init
```

It converts from any existing dep *Gopkg.lock* file or from any of the other nine total supported dependency formats to go module.

## Vendor your modules

```
$ go mod vendor
```

And then add *-mod vendor* in *go build* command.

Example:

```
go build -mod vendor -ldflags "${ldflags}" -o bin/mymicroservice$ ${repo_path}
```

## Clean up dependencies

```
$ go mod tidy
```

## View final versions

They will be used in a build for all direct and indirect dependencies 

```
$ go list -m all
```

## View available minor and patch upgrades for all direct and indirect dependencies

```
$ go list -u -m all
```

## Upgrade dependencies

To upgrade to the latest version for all direct and indirect dependencies of the current module:

* run *go get -u* to use the latest minor or patch releases
* run *go get -u=patch* to use the latest patch releases

Warning: 

A common mistake is thinking go get -u foo solely gets the latest version of foo. In actuality, the -u in go get -u foo or go get -u foo@latest means to also get the latest versions for all of the direct and indirect dependencies of foo. 

## xx

```
$ go list -m -versions my/go/module
```

## xx

```
$ go mod why
```