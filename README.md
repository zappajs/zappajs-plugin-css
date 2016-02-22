#### @with css

`@with css:'cssmod'`

Add a new function named `cssmod` to the [root scope](#root-scope). That function serves CSS compiled from the specified module. Here are two examples with `stylus` and `less`:

    @with css:'stylus'

    @stylus '/foo.css': '''
      border-radius()
        -webkit-border-radius arguments
        -moz-border-radius arguments
        border-radius arguments

      body
        font 12px Helvetica, Arial, sans-serif

      a.button
        border-radius 5px
    '''

Compiles the string with [stylus](http://learnboost.github.com/stylus) and serves the results as `/foo.css`, with content-type `text/css`.

You must have stylus installed with `npm install stylus`.

    @with css:'less'

    @less '/foo.css': '''
      .border-radius(@radius) {
        -webkit-border-radius: @radius;
        -moz-border-radius: @radius;
        border-radius: @radius;
      }

      body {
        font: 12px Helvetica, Arial, sans-serif;
      }

      a.button {
        .border-radius(5px);
      }
    '''

Compiles the string with [less](http://lesscss.org/) and servers the results as '/foo.css', with content-type `text/css`.

You must have less installed with `npm install less`.

