# About Go modules

xxx

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