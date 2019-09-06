# Heroku Multi Procfile buildpack

Imagine you have a single code base, which has a few different applications within it... or at least the ability to run a few different applications. Or, maybe you're Google with your mono repo?

In any case, how do you manage this on Heroku? You don't. Heroku applications assume one repo to one application.

Enter the Monorepo buildpack, which is a copy of [heroku-buildpack-multi-procfile](https://github.com/heroku/heroku-buildpack-multi-procfile) except it moves the target path in to the root, rather than just the Procfile. This helps for ruby apps etc.

# Usage

1. Write a bunch of apps and scatter them through out your code base.
2. Create a bunch of Heroku apps.
3. For each app, set `APP_BASE=relative/path/to/app/root`, and of course:
   `heroku buildpacks:add -a <app> https://github.com/formsort/heroku-buildpack-monorepo`
5. _(Optional)_ add a `bin/heroku-monorepo-prepare` script to make any changes
prior to the structure being changed.
4. For each app, `git push git@heroku.com:<app> master`

# Authors

Andrew Gwozdziewycz <apg@heroku.com>, Cyril David <cyx@heroku.com>, Lincoln Stoll <lstoll@heroku.com> and now Peter Lada <peter@formsort.com>
