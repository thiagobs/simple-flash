# simple-flash
Simple Flash is a very simple way to set flash messages in Express routes.

## Installation

``` sh
npm install simple-flash
```

## Usage

In your app.js (after session setup line):

``` js
var flash = require('simple-flash');
app.use(flash());
```

In your route, only add your messages using the new funcion `req.flash(type,message)`:

``` js
app.post('/foo', function(req, res){
    try {
        // your awesom code here
        req.flash('success','Your success message here!');
        res.redirect('/bar');
    } catch (e){
        req.flash('error','Your error message here!');
        res.redirect('/foo');
    }
})
```

For render messages in view, simpliest use the new local function `flash()` to return messages array:

``` jade
- for(message in flash()){
    div(class="alert-#{message.type}") #{message.message}
- }
```

## For development and tests:

``` sh
git clone https://github.com/thiagobs/simple-flash.git && cd simple-flash
npm install
```

Run tests:

``` sh
npm test
```

## License

[MIT License](http://opensource.org/licenses/MIT)