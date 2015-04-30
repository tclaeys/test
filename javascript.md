#Javascript

**QUESTION**:
*Shall we refer to an existing style guide (Airbnb/jQuery/Google)? Or do we create our own? I'm a little hesitant to link to existing style guides and setting that as our standard.. What if they stop to exist / 404 links? What do you think? I've started setting up our own.*

Table of content:

[TOC]

##Style guide

### Introduction
This style guide is created to enforce a consistent single person coding style for Javascript in a project. **New projects** should adhere to this style unless the project demands a different style due to vendor / framework related code. Key is always to be consistent with the style of the project code.

###Name conventions

- Use **camelCase** when naming objects, functions, and instances.

		var myVar = 1;
		var myNamespace = {};
		var myFunction() {
		
		}

- Use **PascalCase** when naming classes or constructors.

		var myInstance = new Person();

- Use **UPPERCASE** for constants. Use underscore (_) to separate words.
	
		var CONSTANT = 'static';
		var MY_CONSTANT = 'static';

###White space

 - Use indents set to **4 spaces**.
 - TODO: *Do we need to be strict about spaces around expressions?*

###Strings

- Use **single quotes**. Double quotes are only allowed inside single quotes.
- Use string concatenation or Array#join for multi line strings. 
	
		// bad
		var result = 'First line \
					second line \
					third line';

		// good
		var result = 'First line' +
					'second line' + 
					'third line';

		// good
		var result = [
					'First line',
					'second line', 
					'third line',
					].join(',');

###Semicolons
- Use semicolons for termination.

###Comma's
- **No leading** comma's.
	
		// bad
		var obj = {
			prop1: 'value1'
			,prop2: 'value2'
			,prop3: 'value3'
		};
		
		// bad, last trailing comma fails in <= IE8
		var obj = {
			prop1: 'value1',
			prop2: 'value2',
			prop3: 'value3',
		};
		
		// good
		var obj = {
			prop1: 'value1',
			prop2: 'value2',
			prop3: 'value3'
		};


###Variables
- Use a `var` to declare a variable. **Warning**: unassigned variables will become global variables.
- Use a single `var` for a long list of declarations of variables for better readability.

		// bad
		// be aware for mistakes!
		var foo = 'bar',
			lorem = 'ipsum';
			dolor = 'sit';	

		// good
		var foo = 'bar',
			lorem = 'ipsum',
			dolor = 'sit';	

- Variables must be placed on top of their scope to avoid hoisting issues.
- Avoid unused variables.

###Objects
- Use dot notation instead of brackets.

		// bad
		var result = foo['bar'];
		
		// good
		var result = foo.bar;

###Blocks

- Use **braces** for all multi-line blocks. The opening brace starts at the same line.
	
		// bad
		if (foo)
			foo();

		// good
		if (foo) {
			foo();
		}
		
		// bad
		function(foo) { return foo; }

		// good
		function(foo) { 
			return foo;
		}

- 'Else' and 'else if' statements start at the same line as the closing brace.
	
		// bad
		if (foo) {
			bar();
		}
		else {
			bar();
		}
		
		// good
		if (foo) { 
			bar();
		} else {
			bar();
		}
	
		// good
		if (foo) {
			bar();
		} else if (foo) {
			bar();
		} else {
			bar();
		}

- switch/case
	- Use a break for each case other than default.
	- Indent case statements.
		
			switch (foo) {
				case 0:
					bar();
					break;
				case 1:
					bar();
					break;
				default:
					bar();
			} 

### Equality
- Use **strict** equality comparisons. The == and != operators do type coercion before comparing, which can mask type errors. It is best to not use == and != and to always **use the strict === and !== operators** instead.

### Comments
- Use small comments using **//** notation **on top** of the code. Do not use trailing comments. 

		// bad
		var foo = 'bar'; // assign 'bar' value to foo variable
	
		// good
		// assign 'bar' value to foo variable
		var foo = 'bar'; 
	
- Use JSDoc3 comment style for extensive description of code.
- Do not comment out code being under version control, as it bloats programs and reduces readability. 

### Performance
- Use console.time methods to profile the code execution time during development.
- Use jsPerf to run performance Javascript tests across devices and browsers.

### jQuery
- Do not reference the global `$` object variable directly in your code. Use instead function encapsulation to pass in the `jQuery` object variable as parameter making `$` as function argument available within the function scope.

		(function($) {
			
			// Use $ in the scope
		
		})(jQuery);

- Prefix jQuery object variables with $.

		// bad
		var foo = $('#foo');
	
		// good
		var $foo = $('#foo');

- Cache jQuery object variables

		// bad
		$('#foo').css('display', 'none');		
		// ... do something ...
		$('#foo').css('display', 'block');
	
		// good
		var $foo = $('#foo');
		$foo.css('display', 'none');
		// ... do something ...
		$foo.css('display', 'block');	

- Avoid using .show() and .hide() method, but use classes to toggle visibility instead: 
	- https://github.com/jquery/jquery.com/issues/88#issuecomment-72400007
	- http://jsperf.com/jquery-show-hide-vs-css-display-none-block/3

### Quality tools

- JSHint
	- TODO: add link to the Philips JSHINT profile.
- Sonar
	- TODO: add link to the Philips Sonar Javascript profile.
- JSCS 
	- TODO: add link to Philips Javascript Code Style plugin
	- https://medium.com/@addyosmani/auto-formatting-javascript-code-style-fe0f98a923b8
	- http://jscs.info/overview.html
- .EditorConfig
	- TODO: add link to the Philips .EditorConfig file.

##Best practices

### Global variables
Avoid polluting the global scope using global variables. A project may use global variables to expose public functionality, but should be limited to a minimum.
 
### Client side templating
When working with large chunks of strings for HTML generation, use client-side templating to separate concerns (HTML outside JS code) and read-ability. Consider performance impact when choosing for client side templating. Try to pre-compiling templates server-side, before handing them to the browser.

The **{} Mustache** templating syntax is preferred. It's chosen for it's minimalistic approach, requiring to have most logic in models keeping the templates clean. Mustache is widely adopted and supports besides Javascript, most modern server-side languages.  


##Resources
https://github.com/airbnb/javascript
https://github.com/rwaldron/idiomatic.js
http://contribute.jquery.org/style-guide/js/
https://mustache.github.io/mustache.5.html



