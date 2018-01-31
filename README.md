Stylefile
=========
LaTeX style file. Inspiration drawn from Evan Chen.


A LaTeX package differs from a LaTeX class in that it offers the ability to include options. As well, any number of packages can be invoked within one document, whereas classes can be invoked exactly once. A LaTeX package can also be used to invoke other packages. Then, when `\usepackage{<packageName>}` is called, not only will packageName be available, but all the packages it requires too. 

&nbsp;
## Document Structure
The features are defined in roughly the same order of appearance in a would-be pdf rendition. Aside from colour definitions, I start with the title, then the table of contents, then the body. 
&nbsp;
### \ProvidesPackage and \endinput
The document begins with `\ProvidesPackage{<packageName>}[<version>]` (and optionally, a \NeedsTeXFormat{<LaTeX version>}[<version>] statement that specifies the minimum requirements for the user's LaTeX version). It is good form to terminate the file with `\endinput` (Wikibooks says it's required, but I've seen people leave it out).&nbsp;
&nbsp;
### If's
First, the if's are defined; these facilitate the use of options and are set with the syntax: 

```\newif\ifsomecondition\someconditiondefault```

For instance, 

```\newif\ifandrewauthor\andrewauthortrue```

`\newif` is the declaration, `\ifandrewauthor` is the name of the condition, and `\andrewauthortrue` is the default state. The use of 'andrew' here is to prevent conflicts with other packages. 
&nbsp;
### \DeclareOption

`\DeclareOption{<optionName>}{<conditionals>}` will define an optional argument that can change some of the previously defined if's. This optional argument is then called in a .tex file with `\usepackage{<optionName>}{<packageName>}`. In Andrew.sty, I define the 'notes' option:

- ``` \DeclareOption{notes}{\andrewmdthmtrue\andrewspecialsectiontrue\andrewabstracttrue}```
- `\ExecuteOption{<defaultOption>}` selects the default option.
- `\ProcessOptions\relax` terminates the option processing.

&nbsp;  
## TODO

* Correct the \newtheorem* environments and remove italics
* Customize header, footer, and pagenumbering
* Add support for tables and figures
