# dashboard

Engineering Dashboard: 

- JIRA 
- GitHub
- HipChat 
- PagerDuty 
- New Relic 
- Sentry 
- Rollbar 
- Trello
- Docker 


## Usage

To start a local web server for development you can either eval the
commented out forms at the bottom of `web.clj` from your editor or
launch from the command line:

    $ lein run -m dashboard.web

Initialize a git repository for your project.

    $ git init
    $ git add .
    $ git commit -m "Initial commit."

You'll need the [heroku toolbelt](https://toolbelt.herokuapp.com)
installed to manage the heroku side of your app. Once it's installed,
get the app created:

    $ heroku apps:create dashboard
    Creating dashboard... done, stack is cedar
    http://dashboard.herokuapp.com/ | git@heroku.com:dashboard.git
    Git remote heroku added

You can deploy the skeleton project immediately:

    $ git push heroku master
    Writing objects: 100% (13/13), 2.87 KiB, done.
    Total 13 (delta 0), reused 0 (delta 0)

    -----> Heroku receiving push
    -----> Clojure app detected
    -----> Installing Leiningen
           Downloading: leiningen-2.0.0-preview7-standalone.jar
    [...]
    -----> Launching... done, v3
           http://dashboard.herokuapp.com deployed to Heroku

    To git@heroku.com:dashboard.git
     * [new branch]      master -> master

It's live! Hit it with `curl`:

    $ curl http://dashboard.herokuapp.com
    ["Hello" :from Heroku]

The cookie-backed session store needs a session secret configured for encryption:

    $ heroku config:add SESSION_SECRET=$RANDOM_16_CHARS

## Remote REPL

The [devcenter article](https://devcenter.heroku.com/articles/debugging-clojure)
has a detailed explanation, but using the `repl` task from Leiningen
2.x lets you connect a REPL to a remote process over HTTP. The first
step is setting up credentials:

    $ heroku config:add REPL_USER=[...] REPL_PASSWORD=[...]

Then you can launch the REPL:

    $ lein repl :connect http://$REPL_USER:$REPL_PASSWORD@dashboard.herokuapp.com/repl

Everything you enter will be evaluated remotely in the running dyno,
which can be very useful for debugging or inspecting live data.


## Technology 

- Clojue 
- Compojure 
- React 
- Om 
 
Fri Dec  5 10:48:08 EST 2014
