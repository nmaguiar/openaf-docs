---
layout: default
title: ow.template
parent: Reference
grand_parent: OpenAF docs
---


## ow.template

### ow.template.addConditionalHelpers

__ow.template.addConditionalHelpers()__

````
Adds helper functions equivalent to assemble.io comparison helpers. See more in http://assemble.io/helpers/helpers-comparison.html
````
### ow.template.addFormatHelpers

__ow.template.addFormatHelpers()__

````
Adds all functions of ow.format as helpers with the prefix owFormat_.
````
### ow.template.addHelper

__ow.template.addHelper(aHelperName, aFunction)__

````
Adds aFunction as aHelperName.
````
### ow.template.addHelpers

__ow.template.addHelpers(aPrefix, aObject)__

````
Registers all aObject functions as helpers. These helpers identifier will be composed by aPrefix + Name of the each function. 
(available after ow.loadTemplate())
````
### ow.template.addInLineCSS2HTML

__ow.template.addInLineCSS2HTML(aHTML, aCustomCSSMap) : String__

````
Given aHTML (usually the result of parseMD2HTML) applies a custom inline css (aCustomCSSMap) usually useful to send HTML to  email clients. This custom map should be composed of a html tag entity tag (e.g. "p") and, as value, the css style to apply (e.g. "color: red;"). The map will be applied to all html entities on aHTML. If aCustomCSSMap is not provided a default one (suited for markdown html) will be applied.
````
### ow.template.addOpenAFHelpers

__ow.template.addOpenAFHelpers()__

````
Adds custom helpers:

  - debug           -- calls sprint for the parameter
  - stringify       -- stringify the parameter
  - stringifyInLine -- stringify in the same line the parameter
  - toYAML          -- returns the YAML version of the parameter
  - env             -- returns the current environment variable identified by the parameter
  - escape          -- returns an escaped version of the parameter
  - f               -- uses the $f format function
  - ft              -- uses the $ft format function
  - get             -- uses the $$.get function to access objects
  - path            -- uses the $path function to query objects
  - toSLON          -- returns the ow.format.toSLON version of an objecft


````
### ow.template.addPartial

__ow.template.addPartial(aPartialName, aSource)__

````
Registers aSource template as a reusable aPartialName in other templates.
````
### ow.template.compile

__ow.template.compile(aSource, anOptionsMap) : String__

````
Tries to precompile aSource and returns a String that can be used with ow.template.execCompiled. Optionally you can provide anOptionsMap for the Handlebars precompiler (see more on ow.template.saveCompiledHBS).
````
### ow.template.delHelper

__ow.template.delHelper(aHelperName)__

````
Unregister aHelperName that had been previously added with ow.template.addHelper.
````
### ow.template.delPartial

__ow.template.delPartial(aPartialName)__

````
Unregisters aPartialName that had been previously added with ow.template.addPartial
````
### ow.template.execCompiled

__ow.template.execCompiled(aCompiledObject) : Function__

````
Tries to execute a previously precompiled Handlebars template (for example, using ow.template.compile) and return it as a Handlebars template functions.
````
### ow.template.getTemplate

__ow.template.getTemplate(aSource) : Function__

````
Returns a template function, given aSource, that accepts an object as argument and returns the correspoding template filled with the values provided.
````
### ow.template.html.genStaticVersion

__ow.template.html.genStaticVersion(anOriginalHTML) : String__

````
Tries to convert anOriginalHTML with "src" based tags like img, script & stylesheet link tags into a single HTML embeeding  all content.
````
### ow.template.html.genStaticVersion4MD

__ow.template.html.genStaticVersion4MD(anOriginalMD) : String__

````
Tries to convert a markdown into a single HTML embeeding css and image contents.
````
### ow.template.html.genStaticVersion4MDFile

__ow.template.html.genStaticVersion4MDFile(anOriginalMDFile) : String__

````
Tries to convert a markdown file into a single HTML embeeding css and image contents.
````
### ow.template.html.inlineImageTag

__ow.template.html.inlineImageTag(aImageFile, justPartial) : String__

````
Returns a base64 representation of aImageFile to include in markdown/html content. If justPartial = true then only the src  part of the html img tag is returned.
````
### ow.template.html.inlineSrc

__ow.template.html.inlineSrc(aFile, aPrefix, aSuffix) : String__

````
Returns a base64 representation of aFile to include in markdown/html content. If aPrefix and/or aSuffix is provided it will be prefixed and suffixed to the output.
````
### ow.template.html.inlineSrcURL

__ow.template.html.inlineSrcURL(aURL, aPrefix, aSuffix) : String__

````
Returns a base64 representation of aURL to include in markdown/html content. If aPrefix and/or aSuffix is provided it will be prefixed and suffixed to the output.
````
### ow.template.html.parseMap

__ow.template.html.parseMap(aMapOrArray, genParts) : Object__

````
Returns a string with a HTML representation of the aMapOrArray provided or, if genParts = true, a map with the style css and the out string necessary.
````
### ow.template.html.thinFontCSS

__ow.template.html.thinFontCSS(aSize) : String__

````
Returns a CSS string for a thin font with the provided aSize (in points).
````
### ow.template.html.thinFontDiv

__ow.template.html.thinFontDiv(aTxt, aSize, aExtra) : String__

````
Returns a HTML div part to write aTxt with the provided aSize (in points). Optionally aExtra css can be added.
````
### ow.template.html.thinFontSpan

__ow.template.html.thinFontSpan(aTxt, aSize, aExtra) : String__

````
Returns a HTML span part to write aTxt with the provided aSize (in points). Optionally aExtra css can be added.
````
### ow.template.loadCompiledHBS

__ow.template.loadCompiledHBS(aFilename) : Function__

````
Tries to load a previously precompiled Handlebars template (for example, using ow.template.saveCompiledHBS) and return it as a Handlebars template functions.
````
### ow.template.loadHBSs

__ow.template.loadHBSs(aMapOfHBSs) : Function__

````
Given a map where the key is a hbs template key and the value is the filepath of a HBS file, will pre-compile the HBS files and return a function(key, data). This function can be used to execute a the pre-compiled templates using the hbs template key and passing the corresponding data map to be used on that template returning the template parsed. Note: the filepath can indicate a file inside a zip file like 'some/path/a.zip::file'.
````
### ow.template.loadPartialHBS

__ow.template.loadPartialHBS(aMapOfParialHBSs)__

````
Given a map where the key is a partial hbs template key and the value is the filepath of a HBS file, will load it and add it as a template partial. Note: the filepath can indicate a file inside a zip file like 'some/path/a.zip::file'.
````
### ow.template.md.htmlArrayMap

__ow.template.md.htmlArrayMap(anMapOrArray) : String__

````
Converts anMapOrArray into a div html suitable to be added to a markdown.
````
### ow.template.md.table

__ow.template.md.table(anArray) : String__

````
Converts anArray into a markdown table string.
````
### ow.template.parse

__ow.template.parse(aSource, someData) : String__

````
Returns the results of using someData to the template defined on the aSource provided. Note: for parallel processing you should use ow.template.compile since Handlebars might not be thread-safe.
````
### ow.template.parseHBS

__ow.template.parseHBS(aFilename, someData) : String__

````
Returns the results of using someData with the template defined on aFilename (tip: use the extension hbs).
````
### ow.template.parseMD2HTML

__ow.template.parseMD2HTML(aMarkdownString, isFull) : String__

````
Given aMarkdownString will parse it with showdown (using the github flavor) and return the HTML in a string. If isFull = true it will produce a complete HTML with references for the highlight library+css and github markdown css included internally in OpenAF. Example:

ow.server.httpd.route(hs, ow.server.httpd.mapRoutesWithLibs(hs, { 
   "/md": (req) => { return hs.replyOKHTML(ow.template.parseMD2HTML(io.readFileString("README.md"), true)) }
}), (req) => { return hs.replyOKText("nothing here...");})


````
### ow.template.saveCompiledHBS

__ow.template.saveCompiledHBS(aFilename, aSource, anOptionsMap)__

````
Tries to precompile aSource and save the result into aFilename (tip: use the extension hbsc). This can later be loaded again using ow.template.loadCompiledHBS, for example.  Optionally you can provide anOptionsMap for the Handlebars precompiler (see more on the options for Handlebars.precompile). Example:

var source = "My name is {{myname}}. I'm a\n{{#each role}}\t- {{this}}\n{{/each}}";
ow.template.saveCompiledHBS("myroles.hbsc", source, {
   { "knowHelpers": ["each"], "knowHelpersOnly": true }
};


````
### ow.template.saveHBS

__ow.template.saveHBS(aFilename, aSource)__

````
Saves aSource Handlebars template into aFilename (tip: use the extension hbs).
````
### ow.template.unloadPartialHBSs

__ow.template.unloadPartialHBSs(aMapOFPartialHBSs)__

````
Given the same map provided to ow.template.loadPartialHBS will actually unload them as template partials.
````
