# About Go modules

A module is a collection of related Go packages that are versioned together as a single unit.
Modules record precise dependency requirements and create reproducible builds.

Summarizing the relationship between repositories, modules, and packages:

* A repository contains one or more Go modules.
* Each module contains one or more Go packages.
* Each package consists of one or more Go source files in a single directory.

## Initialize a new Go module

You need to execute this command outside GOPATH!

```
$ go mod init github.com/scraly/myproject
```

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
$ go list -u -m all — 
```

## xx

```
$ go list -m -versions my/go/module
```

## xx

```
$ go mod why
```