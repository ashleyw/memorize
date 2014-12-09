Memorize
========

Like async's memoize. But without the rest.

    $ npm install memorize

Example
-------

    var memo = require('memorize');
    
    var foo = memo(function(cb) {
      setTimeout() {
        // this function takes long, long, long
        // but's only going to run once.
        cb('Foo!')
      }, 5000);
    })

    foo(function(msg) {
      console.log(msg); // should take 5 secs

      foo(function(msg) {
        console.log(msg); // immediate
      })
    })

You can also set an expiration time on memoization.

    var foo = memo(function(cb) { 
      // ... (long running method that takes a few seconds)
    }, 7000); // expire after 7 secs.
   
    foo(function(res) {
      // took a while

      foo(function(res) {
        // immediate
      })

      setTimeout(function() {
        foo(function(res) {
          // expiration passed, so function is re-run
        })
      }, 10000);
    })

That's it. For more info take a look at the examples.

About
-----

By Tomás Pollak.
(c) Fork, Ltd. MIT licensed.
