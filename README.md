
# Grant

[![npm-version]][npm] [![coveralls-status]][coveralls]


## 87 Supported Providers / [OAuth Playground][playground]

[`500px`](https://developers.500px.com/) | [`amazon`](http://login.amazon.com/documentation) | [`angellist`](https://angel.co/api) | [`appnet`](https://developers.app.net/reference/resources/) | [`asana`](http://developer.asana.com/documentation/) | [`assembla`](http://api-doc.assembla.com/) | [`basecamp`](https://github.com/basecamp/bcx-api/) | [`bitbucket`](https://confluence.atlassian.com/display/BITBUCKET) | [`bitly`](http://dev.bitly.com) | [`box`](https://developers.box.com/) | [`buffer`](http://dev.buffer.com) | [`cheddar`](https://cheddarapp.com/developer/) | [`coinbase`](https://www.coinbase.com/docs/api/overview) | [`dailymile`](http://www.dailymile.com/api/documentation) | [`dailymotion`](https://developer.dailymotion.com/documentation#graph-api) | [`deezer`](http://developers.deezer.com/) | [`deviantart`](https://www.deviantart.com/developers/) | [`digitalocean`](https://developers.digitalocean.com/) | [`disqus`](https://disqus.com/api/docs/) | [`dropbox`](https://www.dropbox.com/developers) | [`edmodo`](https://developers.edmodo.com/) | [`elance`](https://www.elance.com/q/api2) | [`eventbrite`](http://developer.eventbrite.com/) | [`evernote`](https://dev.evernote.com/doc/) | [`everyplay`](https://developers.everyplay.com/) | [`eyeem`](https://www.eyeem.com/developers) | [`facebook`](https://developers.facebook.com) | [`feedly`](https://developer.feedly.com/) | [`fitbit`](http://dev.fitbit.com/) | [`flattr`](http://developers.flattr.net/) | [`flickr`](https://www.flickr.com/services/api/) | [`flowdock`](https://www.flowdock.com/api) | [`foursquare`](https://developer.foursquare.com/) | [`freshbooks`](https://www.freshbooks.com/developers) | [`geeklist`](http://hackers.geekli.st/) | [`getpocket`](http://getpocket.com/developer/) | [`github`](http://developer.github.com) | [`gitter`](https://developer.gitter.im/docs/welcome) | [`goodreads`](https://www.goodreads.com/api) | [`google`](https://developers.google.com/) | [`harvest`](https://github.com/harvesthq/api) | [`heroku`](https://devcenter.heroku.com/categories/platform-api) | [`imgur`](https://api.imgur.com/) | [`instagram`](http://instagram.com/developer) | [`jawbone`](https://jawbone.com/up/developer/) | [`linkedin`](http://developer.linkedin.com) | [`live`](http://msdn.microsoft.com/en-us/library/dn783283.aspx) | [`mailchimp`](http://apidocs.mailchimp.com/) | [`meetup`](http://www.meetup.com/meetup_api/) | [`mixcloud`](http://www.mixcloud.com/developers/) | [`moves`](https://dev.moves-app.com/) | [`odesk`](https://developers.odesk.com) | [`openstreetmap`](http://wiki.openstreetmap.org/wiki/API_v0.6) | [`paypal`](https://developer.paypal.com/docs/) | [`podio`](https://developers.podio.com/) | [`rdio`](http://www.rdio.com/developers/) | [`redbooth`](https://redbooth.com/api/) | [`reddit`](http://www.reddit.com/dev/api) | [`runkeeper`](http://developer.runkeeper.com/) | [`salesforce`](https://www.salesforce.com/us/developer/docs/api_rest) | [`shopify`](http://docs.shopify.com/api) | [`skyrock`](http://www.skyrock.com/developer/documentation/) | [`slack`](https://api.slack.com/) | [`slice`](https://developer.slice.com/) | [`soundcloud`](http://developers.soundcloud.com) | [`spotify`](https://developer.spotify.com) | [`stackexchange`](https://api.stackexchange.com) | [`stocktwits`](http://stocktwits.com/developers) | [`stormz`](http://developer.stormz.me) | [`strava`](http://strava.github.io/api/) | [`stripe`](https://stripe.com/docs) | [`traxo`](https://developer.traxo.com/) | [`trello`](https://trello.com/docs/) | [`tripit`](https://www.tripit.com/developer) | [`tumblr`](http://www.tumblr.com/docs/en/api/v2) | [`twitch`](https://github.com/justintv/twitch-api) | [`twitter`](https://dev.twitter.com) | [`uber`](https://developer.uber.com/v1/api-reference/) | [`vimeo`](https://developer.vimeo.com/) | [`vk`](http://vk.com/dev) | [`withings`](http://oauth.withings.com/api) | [`wordpress`](https://developer.wordpress.com/docs/api/) | [`xing`](https://dev.xing.com/docs) | [`yahoo`](https://developer.yahoo.com/) | [`yammer`](https://developer.yammer.com/) | [`yandex`](http://api.yandex.com/) | [`zendesk`](https://developer.zendesk.com)


## Table of Contents

- [Express][express]
- [Koa][koa]
- [Hapi][hapi]
- [Reserved Routes for Grant][reserved-routes-for-grant]
- [Configuration][configuration]
- [Redirect Url][redirect-url]
- [Static Overrides][static-overrides]
- [Dynamic Override][dynamic-override]
- [Quirks][quirks]
- [Custom Providers][custom-providers]
- [Development Environments][development-environments]
- [Response Data][response-data]
- [Typical Flow][typical-flow]
- [Get User Profile][get-user-profile]
- [Examples][examples]


## Express

```bash
npm install grant-express
```

```js
var express = require('express')

var Grant = require('grant-express')
  , grant = new Grant({/*configuration see below*/})

var app = express()
// mount grant
app.use(grant)
// other middlewares
app.use(cookieParser())
app.use(session())
```


## Koa

```bash
npm install grant-koa
```

```js
var koa = require('koa')
  , mount = require('koa-mount')
  // https://github.com/simov/grant/tree/master/example/koa-session
  , session = require('any session store')

var Grant = require('grant-koa')
  , grant = new Grant({/*configuration see below*/})

var app = koa()
// required: set the session store before mounting grant!
app.keys = ['keys']
app.use(session(...))
// mount grant
app.use(mount(grant))
// other middlewares
app.use(bodyParser())
```


## Hapi

```bash
npm install grant-hapi
```

```js
var Hapi = require('hapi')
  , yar = require('yar')

var Grant = require('grant-hapi')
  , grant = new Grant()

var server = new Hapi.Server()
server.register([{
  register: grant,
  options: {/*configuration see below*/}
}, {
  register: yar,
  options: {cookieOptions: {password:'password', isSecure:false}}
}], function (err) {
  server.start()
})
```


## Reserved Routes for Grant

```bash
/connect/:provider/:override?
/connect/:provider/callback
```


## Configuration

```js
{
  "server": {
    "protocol": "http",
    "host": "localhost:3000",
    "callback": "/callback",
    "transport": "session",
    "state": true
  },
  "provider1": {
    "key": "...",
    "secret": "...",
    "scope": ["scope1", "scope2", ...],
    "state": "some state",
    "callback": "/provider1/callback"
  },
  "provider2": {...},
  ...
}
```

- **server** - configuration about your server
  - **protocol** - either `http` or `https`
  - **host** - your server's host name `localhost:3000` | `dummy.com:5000` | `mysite.com` ...
  - **callback** - common callback for all providers in your config `/callback` | `/done` ...
  - **transport** - transport to use to deliver the response data in your final callback `querystring` | `session` _(defaults to querystring if omitted)_
  - **state** - generate 6 digit random state number on each authorization attempt `true` | `false` _(OAuth2 only, defaults to false if omitted)_
- **provider1** - any [supported provider][grant] `facebook` | `twitter` ...
  - **key** - `consumer_key` or `client_id` of your app
  - **secret** - `consumer_secret` or `client_secret` of your app
  - **scope** - array of OAuth scopes to request
  - **state** - OAuth state string to send
  - **callback** - specific callback to use for this provider _(overrides the global one specified under the `server` key)_

_(additionally any of the [reserved keys][reserved-keys] can be overriden for a provider)_


## Redirect Url

For `callback/redirect` url of your OAuth application you should **always** use this format

```
[protocol]://[host]/connect/[provider]/callback
```

Where `protocol` and `host` should match the ones from which you initiate the OAuth flow, and `provider` is the provider's name from the list of [supported providers][grant]

This `redirect` url is used internally by Grant. You will receive the [response data][response-data] from the OAuth flow in the route specified in the `callback` key of your Grant configuration


## Static Overrides

You can add arbitrary _{object}_ keys inside your provider's configuration to create sub configurations that override the _global_ settings for that provider

```js
// navigate to /connect/facebook
"facebook": {
  "key": "...",
  "secret": "...",
  // by default request publish permissions
  "scope": ["publish_actions", "publish_stream"],
  // set specific callback route on your server for this provider
  "callback": "/facebook/callback"
  // navigate to /connect/facebook/groups
  "groups": {
    // request only group permissions
    "scope": ["user_groups", "friends_groups"]
  },
  // navigate to /connect/facebook/pages
  "pages": {
    // request only page permissions
    "scope": ["manage_pages"],
    // additionally use specific callback route on your server for this override
    "callback": "/facebook_pages/callback"
  }
}
```

_(these custom key names should be different than the [reserved ones][reserved-keys])_


## Dynamic Override

Additionally you can make a `POST` request to the `/connect/:provider/:override?` route to override your provider's configuration dynamically on each request

```html
<form action="/connect/facebook" method="post" accept-charset="utf-8">
  <input name="state" type="text" value="" />
  <input name="scope" type="checkbox" value="read" />
  <input name="scope" type="checkbox" value="write" />
  <button>submit</button>
</form>
```

Alternatively you can use a `GET` request with the `/connect/:provider/:override?` route

```js
app.get('/connect_facebook', function (req, res) {
  // generate random state parameter on each authorization attempt
  var state = (Math.floor(Math.random() * 999999) + 1)

  res.redirect('/connect/facebook?state=' + state)
})
```


## Quirks

- To use the LinkedIn's OAuth2 flow you should use `linkedin2` as a provider name, instead of `linkedin` which is for OAuth1
- For Freshbooks, Shopify and Zendesk you should specify your company's sub domain name through the `subdomain` option
- Some providers may employ custom authorization parameters outside of the ones specified in the [configuration][configuration] section. You can pass those custom parameters directly in your configuration, for example: Google - `access_type:'offline'`, Reddit - `duration:'permanent'`, Trello - `expiration:'never'`, and so on. Refer to the provider's OAuth documentation, and the Grant's [OAuth configuration][oauth-config] (search for `custom_parameters`)


## Custom Providers

In case you have a private OAuth provider that you don't want to be part of the [officially supported][oauth-config] ones, you can still define it in your configuration by adding a custom key for it

In this case you have to provide all of the required provider keys by yourself. Take a look at the [OAuth configuration][oauth-config] to see how the different types of flows are configured

```js
{
  "server": {
    "protocol": "https",
    "host": "mywebsite.com"
  },
  "custom1": {
    "authorize_url": "https://mywebsite.com/authorize",
    "access_url": "https://mywebsite.com/token",
    "oauth": 2,
    "key": "client_id",
    "secret": "client_secret",
    "scope": ["read", "write"]
  }
}
```


## Development Environments

You can easily configure different development environments

```js
{
  "development": {
    "server": {"protocol": "http", "host": "dummy.com:3000"},
    "facebook": {
      "key": "development OAuth app credentials",
      "secret": "development OAuth app credentials"
    },
    "twitter": {...}, ...
  },
  "staging": {
    "server": {"protocol": "https", "host": "staging.mywebsite.com"},
    "facebook": {
      "key": "staging OAuth app credentials",
      "secret": "staging OAuth app credentials"
    },
    "twitter": {...}, ...
  },
  "production": {
    "server": {"protocol": "https", "host": "mywebsite.com"},
    "facebook": {
      "key": "production OAuth app credentials",
      "secret": "production OAuth app credentials"
    },
    "twitter": {...}, ...
  }
}
```

Then you can pass the environment flag

```bash
$ NODE_ENV=production node app.js
```

And use it in your application

```js
var config = require('./config.json')
var grant = new Grant(config[process.env.NODE_ENV||'development'])
```


## Response Data

The OAuth data is returned as a querystring in your **final** callback _(the one you specify in the `callback` key of your Grant configuration)_

Alternatively the response data can be returned in the session, see the [configuration][configuration] section above and the [session transport][session-transport-example] example


#### OAuth1

For OAuth1 the `access_token` and the `access_secret` are accessible directly, `raw` contains the raw response data

```js
{
  access_token:'...',
  access_secret:'...',
  raw:{
    oauth_token:'...',
    oauth_token_secret:'...',
    some:'other data'
  }
}
```


#### OAuth2

For OAuth2 the `access_token` and the `refresh_token` (if present) are accessible directly, `raw` contains the raw response data

```js
{
  access_token:'...',
  refresh_token:'...',
  raw:{
    access_token:'...',
    refresh_token:'...',
    some:'other data'
  }
}
```


#### Error

In case of an error, the `error` key will be populated with the raw error data

```js
{
  error:{
    some:'error data'
  }
}
```


## Typical Flow

1. Register OAuth application on your provider's web site
2. For `callback/redirect` url **always** use this format
  `[protocol]://[host]/connect/[provider]/callback`
3. Create a `config.json` file containing

  ```js
  "server": {
    "protocol": "https",
    "host": "mywebsite.com"
  },
  "facebook": {
    "key": "[APP_ID]",
    "secret": "[APP_SECRET]",
    "callback": "/handle_facebook_response"
  },
  "twitter": {
    "key": "[CONSUMER_KEY]",
    "secret": "[CONSUMER_SECRET]",
    "callback": "/handle_twitter_response"
  }
  ```
4. Initialize Grant and mount it

  ```js
  // Express
  var express = require('express')
    , Grant = require('grant-express')
    , grant = new Grant(require('./config.json'))
  var app = express()
  app.use(grant)
  // or Koa (see above)
  // or Hapi (see above)
  ```
5. Navigate to `/connect/facebook` to initiate the OAuth flow for Facebook, or navigate to `/connect/twitter` to initiate the OAuth flow for Twitter
6. Once the OAuth flow is complete you will receive the response data in the `/handle_facebook_response` route for Facebook, and in the `/handle_twitter_response` route for Twitter

_(also take a look at the [examples][examples])_


## Get User Profile

Once you have your access tokens secured, you can start making authorized requests on behalf of your users. _**[Purest][purest]**_ is a great REST API library that supports **dozens** of REST API providers

For example, you may want to get the user's profile after the OAuth flow has completed

```js
var Purest = require('purest')
  , facebook = new Purest({provider:'facebook'})
  , twitter = new Purest({provider:'twitter',
    key:'[CONSUMER_KEY]', secret:'[CONSUMER_SECRET]'})

facebook.query()
  .get('me')
  .auth('[ACCESS_TOKEN]')
  .request(function (err, res, body) {
    // here body is a parsed JSON object containing things such as
    // id, first_name, last_name, gender, username and so on
  })

twitter.query()
  .get('users/show')
  .qs({screen_name:'nodejs'})
  .auth('[ACCESS_TOKEN]', '[ACCESS_SECRET]')
  .request(function (err, res, body) {
    // here body is a parsed JSON object containing things such as
    // id, screen_name and so on
  })
```


## License

MIT


  [playground]: https://grant-oauth.herokuapp.com/
  [purest]: https://github.com/simov/purest
  [request]: https://github.com/request/request

  [npm]: https://www.npmjs.org/package/grant
  [travis]: https://travis-ci.org/simov/grant
  [coveralls]: https://coveralls.io/r/simov/grant?branch=master

  [npm-version]: http://img.shields.io/npm/v/grant.svg?style=flat-square (NPM Version)
  [npm-downloads]: http://img.shields.io/npm/dm/grant.svg?style=flat-square (NPM Downloads)
  [travis-ci]: https://img.shields.io/travis/simov/grant/master.svg?style=flat-square (Build Status)
  [coveralls-status]: https://img.shields.io/coveralls/simov/grant.svg?style=flat-square (Coveralls Status)

  [oauth-config]: https://github.com/simov/grant/blob/master/config/oauth.json
  [reserved-keys]: https://github.com/simov/grant/blob/master/config/reserved.json

  [examples]: https://github.com/simov/grant/tree/master/example
  [session-transport-example]: https://github.com/simov/grant/blob/master/example/session-transport/app.js

  [grant]: #grant
  [table-of-contents]: #table-of-contents
  [express]: #express
  [koa]: #koa
  [hapi]: #hapi
  [reserved-routes-for-grant]: #reserved-routes-for-grant
  [configuration]: #configuration
  [redirect-url]: #redirect-url
  [static-overrides]: #static-overrides
  [dynamic-override]: #dynamic-override
  [quirks]: #quirks
  [custom-providers]: #custom-providers
  [development-environments]: #development-environments
  [response-data]: #response-data
  [typical-flow]: #typical-flow
  [get-user-profile]: #get-user-profile
