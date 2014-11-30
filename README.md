Meteor CodeMirror package
=========================

<a href="http://codemirror.net/" target="_blank">CodeMirror</a> packaged for Meteor. **CodeMirror** is a versatile text editor implemented in JavaScript for the browser.


Usage
-----

Put somewhere in your template:

```
<template name="EditorPage">

	{{> CodeMirror id="some-id" name="someName" options=editorOptions code=editorCode}}

</template>
```

Parameters:

- `id` will be set to internal textarea element

- `name` will be set to internal textarea element (useful in form submit)

- `options` is CodeMirror options object

- `code` is code to show in editor


And provide helpers that returns CodeMirror options and content:

```
Template.EditorPage.helpers({

	"editorOptions": function() {
		return {
			lineNumbers: true,
			mode: "javascript"
		}
	},

	"editorCode": function() {
		return "Code to show in editor";
	}

});
```

To get value from editor, just read value from the internal textarea:

```
Template.EditorPage.events({

	"some event": function(e, t) {
		var code = t.find("#some-id").value;
		alert(code);
	}

});

```


Or, using raw html/javascript
-----------------------------

Create textarea somewhere in your html template:

```
<template name="EditorPage">

	<textarea id="myTextarea"></textarea>

</template>
```

Initialize CodeMirror somewhere from your js:

```
Template.EditorPage.rendered = function() {
	var editor = CodeMirror.fromTextArea(this.find("#myTextarea"), {
		lineNumbers: true,
		mode: "javascript" // set any of supported language modes here
	});
}
```

Deal with textarea as you normaly do with textarea, with exception that you cannot directly style `textarea` element - so, wrap it into `div` (that's because your textarea will be hidden and replaced by CodeMirror's own markup).


Supported modes
---------------

```
apl
asterisk
clike
clojure
cobol
commonlisp
coffeescript
css
cypher
d
diff
django
dtd
dylan
ecl
eiffel
erlang
fortran
gas
gfm
gherkin
go
groovy
haml
haskell
haxe
htmlembedded
htmlmixed
http
idl
jade
javascript
jinja2
julia
kotlin
livescript
lua
markdown
mirc
mllike
modelica
nginx
ntriples
octave
pascal
pegjs
perl
php
pig
properties
puppet
python
q
r
rpm
rst
ruby
rust
sass
scheme
shell
sieve
slim
smalltalk
smarty
smartymixed
solr
sparql
sql
stex
tcl
textile
tiddlywiki
tiki
toml
tornado
turtle
vb
vbscript
velocity
verilog
xml
xquery
yaml
z80
```


Supported themes
----------------

```
3024-day
3024-night
ambiance-mobile
ambiance
base16-dark
base16-light
blackboard
cobalt
eclipse
elegant
erlang-dark
lesser-dark
mbo
mdn-like
midnight
monokai
neat
neo
night
paraiso-dark
paraiso-light
pastel-on-dark
rubyblue
solarized
the-matrix
tomorrow-night-eighties
twilight
vibrant-ink
xq-dark
xq-light
```


Supported key bindings
----------------------

```
emacs
sublime
vim
```

Supported "lints"
-----------------

```
javascript
json
css
```


That's it.
