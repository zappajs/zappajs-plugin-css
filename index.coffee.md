ZappaJS Plugin: Extend the context with CSS rendering

    invariate = require 'invariate'

    module.exports = zappajs_plugin_css = (modules) ->
      {context,route} = this
      if typeof modules is 'string'
        modules = [modules]
      for name in modules
        module = @require(name)
        context[name] = invariate (k,v) ->
          module.render v, filename: k, (err, css) ->
            throw err if err
            css = css.css if css.css? and typeof css.css is 'string' # less
            route verb: 'get', path: k, handler: css, type: 'css'
          return
      return
