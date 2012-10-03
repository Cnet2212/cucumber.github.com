This is the source of the new http://cukes.info site

## Contributing

There are two ways you can contribute: By improving content or by improving design. Both happen via [pull requests](https://help.github.com/articles/using-pull-requests).

### Improving the content

There should be `*.md` files lying arounf that don't have a lot of content in them. Feel free to add content here.
You don't actually have to fork or clone his repo to do that---you can edit content straight in your browser by going to [http://prose.cukes.info](http://prose.cukes.info). From there you will be able to send a pull request as well.

You can also add new `.md` pages, but if you do, please update the navigation menu as well---you'll find it in `_config.yml`.

Keep in mind that this site aims to document everything Cucumber in a platform neutral way, so if you're adding code, please use a tab pane so that users can see code examples in various programming languages. You don't have to add code for all languages, we'll do our best to fill that in afterwards.

### Improving the design

If you wish to make changes to the design you need to build the site locally.
First, [fork](https://help.github.com/articles/fork-a-repo) this repo and clone your own fork.

Now that you have the code, get the submodules:

```
git submodule update --init --recursive
```

#### Twitter Bootstrap

This will pull in a [fork of Twitter Bootstrap](https://github.com/cucumber/bootstrap) under `vendor/bootstrap`. This fork has some modifications from the official Bootstrap - mainly in `variables.less`.

If you make changes to Bootstrap you have to rebuild it. Standing in `vendor/bootstrap`, run:

```
# Check Bootstrap's README for detailed build instructions
make build clean bootstrap

# Alternatively, you can build automatically when you save a .less file
# in which case you should set bootstrap_min: false in _config.yml
make watch
```

This should make some changes in the compiled files as well - `vendor/bootstrap/bootstrap`. In the official Bootstrap repo this directory isn't added to git (it's generated), but for our fork it's added to git. This makes the compiled bootstrap CSS and JavaScript available to the live site when it's pushed to [Github Pages](http://pages.github.com/), because it automatically [fetches submodules](https://help.github.com/articles/using-submodules-with-pages).

#### Contributing your Twitter Bootstrap changes

Unfortunately, due to the nature of Git, you'll have to push any changes to Bootstrap to your own fork of [Cucumber's Bootstrap](https://github.com/cucumber/bootstrap). Assuming you have only forked this repo (`https://github.com/cucumber/cucumber.github.com`), you also need to fork `https://github.com/cucumber/bootstrap`.

When you have done that, add a remote to *your* fork when you're standing in the `vendor/bootstrap` directory:

```
git remote add YOURUSER git@github.com:YOURUSER/bootstrap.git
```

Now you can push your changes to your fork:

```
git push YOURUSER master
```

And it's time to send a pull request!
