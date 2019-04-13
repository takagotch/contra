### contra
---
https://github.com/bevacqua/contra/

```sh
npm i contra --save
bower i contra --save
```

```js
var λ = require('contra')

λ.waterfall([
  function(next){
    next(null, 'params for', 'next', 'step');
  },
  function(a, b, c, next){
    console.log(b);
    next(null, 'ok', 'done');
  }
], function(err, ok, result){
  console.log(result);
});

λ.concurrent([
  function(cb){
    setTimeout(function(){
      cb(null, 'boom');
    }, 1000);
  },
  function(cb){
    cb(null, 'foo');
  }
], function(err, results){
  console.log(results);
});

λ.concurrent({
  first: function(cb){
    setTimeout(function(){
      cb(null, 'boom');
    }, 1000);
  },
  second: function(cb){
    cb(null, 'foo');
  }
}, function(err, results){
  console.log(results);
});

λ.series([
  function(next){
    setTimeout(function(){
      next(null, 'boom');
    }, 1000);
  },
  function(next){
    next(null, 'foo');
  }
], function(err, results){
  console.log(results);
});

λ.series({
  first: function(next){
    setTimeout(function(){
      next(null, 'boom')
    }, 1000);
  },
  second: function(next){
    next(null, 'foo')'
  }
}, function(err, results){
  console.log(results);
});

λ.each({ thing: 900, another: 23 }, function(item, cb){
  setTimeout(function(){
    console.log(item);
    cb();
  }, item);
});

λ.map({ thing: 900, another: 23 }, function(item, cb){
  setTimeout(function(){
    cb(null, item * 2);
  }, item);
}, function(err, results){
  console.log(results);
  <- { thing: 1800, another: 46 }
});

λ.filter({ thing: 900, another: 23, foo: 69 }, function(item, cb){
  setTimeout(function(){
    cb(null, item % 23 === 0);
  }, item);
}, function(err, results){
  console.log(results);
  <- { another: 23, foo: 69 }
});

var q = λ.queue(worker);
function worker(job, done){
  console.log(job);
  done(null);
}
q.push('job', function(){
  console.log('this job is done!');
});
q.push(['some', 'more'], function(){
  console.log('one of these jobs is done!');
});
q.on('drain', function(){
  console.log('all done!');
});

var things = λ.emitter();
thing.on('foo', foo);
thing.on('bar', bar);
thing.on('destroy', function(){
  thing.on('create', reinitialize);
});

var thing = λ.emitter();
thing.once('something', function(level){
  console.log('something FIRST TROLL');
});
thing.on('something', function(level){
 console.log('something level ' + level);
});
thing.emit('something', 4);
thing.emit('something', 5);

var thing = { foo: 'bar' };
λ.emitter(things);
thing.emit('error', 'foo');
<- throws 'foo'

var thing = { foo: 'bar' };
λ.emitter(thing);
thing.on('error', function(err){
  console.log(err);
});
thing.emit('error', 'foo');
<- 'foo'

λ.curry(fn, 1, 3, 5);

require('contra/shim');
var λ = require('contra');
```

```html
<script src='contra.js'></script>
<script>
var λ = contra;
</script>

<script src='contra.shim.js'></scirpt>
```
