## Information

This gulp plugin is based on Sindre Sorhus gulp-mocha plugin, but pointing to [mocha-co](https://www.npmjs.org/package/mocha-co)

## Use
In order to have your tests running with mocha-co you need to launch gulp with the ES6 flag '--harmony'

You can do it with
````
node --harmony `which gulp`
````
or creating an alias
````
alias gulp='node --harmony `which gulp`'
````

Then you can run your tasks as normal

````
gulp test
````


## Install

Install with [npm](https://npmjs.org/package/gulp-mocha-co)

```
npm install --save-dev gulp-mocha-co
```

## Example

```js
var gulp = require('gulp');
var mocha = require('gulp-mocha-co');

gulp.task('default', function () {
  gulp.src('test.js')
    .pipe(mocha({reporter: 'nyan'}));
});
```

## Code with generators

```js

describe('My test with generators', function(){
  before(function *(){
    yield whatever.doSomething()
  });

  beforeEach(function(){
    var returnedThing = yield whatever.returnWhatever()
  });

  it('Should have the things', function*(){
    var thingsExist = yield parser.checkIfThingsExist();
    expect(thingsExist).to.equals(true);
  });
});

```


## API

### mocha(options)


#### options.ui

Type: `String`  
Default: `bdd`  
Values: `bdd`, `tdd`, `qunit`, `exports`

The interface to use.


#### options.reporter

Type: `String`  
Default: `dot`  
Values: [reporters](https://github.com/visionmedia/mocha/tree/master/lib/reporters)

The reporter that will be used.

This option can also be used to utilize third-party reporters. For example if you `npm install mocha-lcov-reporter` you can then do use `mocha-lcov-reporter` as value.


#### options.globals

Type: `Array`

Accepted globals.


#### options.timeout

Type: `Number`  
Default: `2000`

Test-case timeout in milliseconds.


#### options.bail

Type: `Boolean`  
Default: `false`

Bail on the first test failure.


#### options.ignoreLeaks

Type: `Boolean`  
Default: `false`

Ignore global leaks.


#### options.grep

Type: `String`

Only run tests matching the given pattern which is internally compiled to a RegExp.


## License
Based on Sindre Sorhus work
MIT © [Sindre Sorhus](http://sindresorhus.com)
