Express-Liquid [![Build Status](https://secure.travis-ci.org/leizongmin/express-liquid.png?branch=master)](http://travis-ci.org/leizongmin/express-liquid) [![Dependencies Status](https://david-dm.org/leizongmin/express-liquid.png)](http://david-dm.org/leizongmin/express-liquid)
==============


Install
=======

```bash
npm install express-liquid
```


Using TinyLiquid in Express 3.x
===============================

1.Setting template engine

```javascript
var expressLiquid = require('express-liquid');
var options = {
  // read file handler, optional
  includeFile: function (filename, callback) {
    fs.readFile(filename, 'utf8', callback);
  }
  // the base context, optional
  context: expressLiquid.newContext(),
  // custom tags parser, optional
  customTags: {}
};
app.set('view engine', 'liquid');
app.engine('liquid', expressLiquid(options));
```

More about **TinyLiquid**, see https://github.com/leizongmin/tinyliquid

2.Render template

```javascript
res.render('template_name', {context: context});
```

3.About **include** tag: {% include %}

The root directory is **views**, for example: {% include "abc/efg" %} will include the file "abc/edf" under the "views" directory

If your want to use a relative file path, please add the "./" or "../" prefix. For example:

```
{% include "./path/to" %}
{% include "../path/to" %}
```

4.Usually, you may omit template file name suffix, then it will try to add a subffix name from the configuration `view engine`


License
=======

You can feel free to use and distribute it under the premise of compliance with the **MIT Licence**.

    Copyright (c) 2012-2013 Lei Zongmin <leizongmin@gmail.com>
    http://ucdok.com
    
    The MIT License
    
    Permission is hereby granted, free of charge, to any person obtaining
    a copy of this software and associated documentation files (the
    "Software"), to deal in the Software without restriction, including
    without limitation the rights to use, copy, modify, merge, publish,
    distribute, sublicense, and/or sell copies of the Software, and to
    permit persons to whom the Software is furnished to do so, subject to
    the following conditions:
    
    The above copyright notice and this permission notice shall be
    included in all copies or substantial portions of the Software.
    
    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
    EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
    MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
    NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
    LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
    OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
    WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
