### Go Modules

Go Modules introduce new way to manage dependencies but also new hurdles
of using them. In here we will gather knowledge, tools and other bits to ease up use of
go modules.


#### Updating modules

To simply update dependency to newer tagged version:
```
go get github.com/ipfs/go-cid@v0.0.2
```

It is not required to update all after a new version is released.
In general update update modules that use the new functionality or require fixes.

##### Dev workflow

Use local replace [directives](https://github.com/golang/go/wiki/Modules#when-should-i-use-the-replace-directive) for developing.
Example:
```
replace github.com/ipfs/go-cid => ../go-cid
```

To test out in CI, commit and push the dependency to a branch and then run:
```
go get github.com/ipfs/go-cid@$HASH
```
to update the version. You can also replace `$HASH` with branch name.

If for some reason version in the build did not change
(caused by off master tags). Use replace directive like this:
```
replace github.com/ipfs/go-cid => github.com/ipfs/go-cid@$HASH
```


#### CI Config

Here is a config for Travis CI: [travis.example.yml](https://github.com/ipfs/ci-helpers/blob/master/travis-ci/travis.example.yml)

#### Git hook to prevent pushing local replace directives

The [pre-commit](https://gist.github.com/Kubuxu/3fc5639db27f4b072b33a84b51048ff8)
hook will alert you, when you are trying to commit go.mod file with local replace directives.
This is useful pattern for developing but has no place on remote.

It is best to install it as global githook. Instructions [here](https://stackoverflow.com/questions/1977610/change-default-git-hooks/37293001#37293001)


