## JS-Speed (bandwidth speed)

This is a minimal source to estimate **bandwidth** using [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) and (or) [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)


See **Considerations** section about

## Set:

Add before `</body>` tag e.g:

```html
   <body>
       <!-- your content -->
       
       <script src="./js-speed.js"></script>
   </body>
```
>
> NOTE: default script return function constructor and result Promise but add query args change this
>

```html
    <script src="./js-speed?promise=false"></script>
    <!--
        This add JsSpeed to window.navigator scope
            - access: window.navigator.JsSpeed // output e.g: 472.68 kb/s
    -->
    
    <script src="./js-speed?promise=false&strict=false"></script>
    <!--
        This add JsSpeed to global scope (see note)
            - access: JsSpeed // output e.g: 472.68 kb/s
    -->
```

Querystring `key: values` represent {object} with `boolean` ( promise | strict | cached | log)


**Options note:**

If you use a custom **uri**: note **CORS Policy** [or throw error]

If you use a custom **timeout**: don't recomend us values beetwen 1 and 1000 (milliseconds) [or throw error timeout]

If you use a custom **cached**: next request from browser cache [inconsistent metric result]


>
> NOTE: **ONLY USE IF NOT** "use strict" mode
>
> When trying to assign a value to a name without using the var keyword, Javascript tries to locate
> the named reference in what the ECMAScript spec calls "[LexicalEnvironment](http://www.ecma-international.org/ecma-262/5.1/#sec-10.3)", and the main difference is that
> LexicalEvironments are nested - that is a LexicalEnvironment has a parent (what the ECMAScript spec calls "outer environment reference")
> and when Javscript fails to locate the reference in a LexicalEenvironment, it looks in the parent
> LexicalEnvironment (as detailed in [10.3.1](http://www.ecma-international.org/ecma-262/5.1/#sec-10.3.1) and [10.2.2.1](http://www.ecma-international.org/ecma-262/5.1/#sec-10.2.2.1)).
> The top level LexicalEnvironment is the "[global environment](http://www.ecma-international.org/ecma-262/5.1/#sec-10.2.3)", and that is bound to the global object in that its
> references are the global object's properties.
> So if you try to access a name that was not declared using a var keyword in the current scope or any outer scopes,
> Javascript will eventually fetch a property of the window object to serve as that reference.
>
> [see best reference on stackoverflow.com](https://stackoverflow.com/questions/1596782/how-to-unset-a-javascript-variable)


## Usage:

```javascript
    // with constructor
    var speed = new JsSpeed(/*options*/);
    // Promise
    speed.test(/*rewrite constructor options*/)
    .then(res=>{
        console.log(res); // output e.g: 472.68 Kb/s
    })
    .catch(e=>{
        console.log(e); // output e.g: timeout end|request error(s)
    });
    
    // with window.navigator
    console.log(window.navigator.JsSpeed); // output e.g: 472.68 Kb/s
    
    // or with global
    console.log(JsSpeed); // output e.g: 472.68 Kb/s
    
    // white jQuery (Promise)
    $.JsSpeed(/*options*/)
    .then(function(res){
        console.log(res); // output e.g: 472.68 Kb/s
    })
    catch(...)
```


## To Do

- [X] add prettybytes function to more than of 1000.00 kb/s (MB) e.g: 1.2 Mb/s


## Contribute

You want to improve the code? Send your **pull request**!

Found a mistake? Got a question or a suggestion? [open new issue](https://github.com/subversivo58/js-speed/issues/new)!

**All collaboration is welcome!**


## Considerations:

This source code does not allow actual capture of the connection bandwidth, it only estimates based on the initial request time file size and response time.
Use caution while observing the following questions:

* latency in the connection between servers
* timming response between servers
* issues not considered in this development


## Attribution:

Default resource link **"uri"** (because CORS and cause: Open Source)

>
> Logo Open Source Initiative (SVG)
>
> Creative Commons Attribution 2.5 - 2014 Open Source Initiative official SVG
>
> By Open Source Initiative official SVG (Simon Phipps, former president of OSI)
> [CC BY 2.5 (http://creativecommons.org/licenses/by/2.5)], via Wikimedia Commons
>

         
## License

(The MIT License)

Copyright (c) 2017 Lauro Moraes [[A.K.A. Subversivo58]](https://github.com/subversivo58)

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
