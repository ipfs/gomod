### Go Modules

Go Modules introduce new way to manage dependencies but also new hurdles
of using them. In here we will gather knowledge, tools and other bits to ease up use of
go modules.


#### CI Config

Here is a config for Travis CI: [travis.example.yml](https://github.com/ipfs/ci-helpers/blob/master/travis-ci/travis.example.yml)

#### Git hook to prevent pushing local replace directives

The [pre-commit](https://gist.github.com/Kubuxu/3fc5639db27f4b072b33a84b51048ff8)
hook will alert you, when you are trying to commit go.mod file with local replace directives.
This is useful pattern for developing but has no place on remote.

It is best to install it as global githook. Instructions [here](https://stackoverflow.com/questions/1977610/change-default-git-hooks/37293001#37293001)


