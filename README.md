# Blog about some stuff

Blog written using [Jekyll]

# Synopsis

Test locally using [Jekyll Docker] container.

```bash
$ git clone https://github.com/kwakwaversal/kwakwaversal.github.io.git $HOME/kwakwaversal.github.io
$ docker run -it --rm -v $HOME/kwakwaversal.github.io:/pwd -w /pwd -p 4000:4000 jekyll/jekyll jekyll serve
```

# Description

These pages are a work in progress. The hope is that I will be articulating
the things I discover when following the black hole after I get a thought in
my head.

# References

* [Jekyll directory structure](https://jekyllrb.com/docs/structure/)
* [Jekyll writing posts](https://jekyllrb.com/docs/posts/)
* [Jekyll whitelisted plugins](https://help.github.com/articles/configuring-jekyll-plugins/#default-plugins)

[Jekyll]: https://jekyllrb.com/
[Jekyll Docker]: https://github.com/envygeeks/jekyll-docker/blob/master/README.md
