An [Heroku](http://www.heroku.com/) [buildpack](https://devcenter.heroku.com/articles/buildpack-api) to install [graphviz](http://www.graphviz.org/).

# Usage

## Alone

Execute following command to use `buildpack-graphviz` as buildpack:

```
heroku config:add BUILDPACK_URL=https://github.com/jeluard/heroku-buildpack-graphviz.git
```

## With other buildpacks

You certainly want to do something more than just using graphviz. You will then have to use other build packs. This can be achieved with [buildpack-graphviz](https://github.com/ddollar/heroku-buildpack-multi).

Add all needed buildpacks to your `.buildpacks`:

```
https://github.com/jeluard/heroku-buildpack-graphviz.git
... # all others buildpacks
```

Use `buildpack-multi` as buildpack:

```
heroku config:add BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git
```

Due to a buildpack-multi [limitation](https://github.com/ddollar/heroku-buildpack-multi/issues/5) variables exported by all but last defined buildpack will be ignored.
An easy workaround is to define graphviz buildpack first then manually export variable:

```
heroku config:add LD_LIBRARY_PATH=.graphviz/lib/
```