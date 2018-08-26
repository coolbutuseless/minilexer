
*minilexer*: A Simple Lexer in R
==============================================================================





`minilexer` provides a tool for simple tokenising/lexing of text files.  

`minilexer` aims to be great at helping to get unsupported text data formats into R *fast*. 

For complicated parsing (especially of computer programs) you'll want to use the more formally correct lexing/parsing provided by the [`rly` package](https://cran.r-project.org/package=rly) or the [`dparser` package](https://cran.r-project.org/package=dparser).

Note: As of version 0.1.6, the `TokenStream` handler has been removed. Use `ministreamer::NamedValueStream` instead.


Installation
-----------------------------------------------------------------------------

```r
devtools::install_github('coolbutuseless/minilexer')
```



Package Overview
-----------------------------------------------------------------------------


Current the package provides one function:

* `minilexer::lex(text, patterns)` for splitting the text into tokens.
    * This function uses the user-defined regular expressions (`patterns`) to split 
      `text` into a character vector of tokens.
    * The `patterns` argument is a named vector of character strings representing regular
      expressions for elements to match within the text.  




Introducing the `minilexer` package
-----------------------------------------------------------------------------

`minilexer` provides a tool for simple tokenising/lexing text files.

I will emphasise the **mini** in `minilexer` as this is not a rigorous or formally complete lexer, but it
suits 90% of my needs for turning data text formats into tokens.

For complicated parsing (especially of computer programs) you'll probably want to use the more formally correct lexing/parsing provided by the [`rly` package](https://cran.r-project.org/package=rly) or the [`dparser` package](https://cran.r-project.org/package=dparser).



Installation
-----------------------------------------------------------------------------

```r
devtools::install_github('coolbutuseless/minilexer')
```



Package Overview
-----------------------------------------------------------------------------

Current the package provides just one function: 

* `minilexer::lex(text, patterns)` for splitting the text into tokens.
    * This function uses the user-defined regular expressions (`patterns`) to split 
      `text` into a character vector of tokens.
    * The `patterns` argument is a named vector of character strings representing regular
      expressions for elements to match within the text.  


Example: Use `lex()` to split sentence into tokens
-----------------------------------------------------------------------------

```r
sentence_patterns <- c(
  word        = "\\w+", 
  whitespace  = "\\s+",
  fullstop    = "\\.",
  comma       = ","
)

sentence = "Hello there, Rstats."

lex(sentence, sentence_patterns)
```

```
##       word whitespace       word      comma whitespace       word 
##    "Hello"        " "    "there"        ","        " "   "Rstats" 
##   fullstop 
##        "."
```



Example: Use `lex()` to split some simplified R code into tokens
-----------------------------------------------------------------------------


```r
R_patterns <- c(
  number      = "-?\\d*\\.?\\d+",
  name        = "\\w+",
  equals      = "==",
  assign      = "<-|=",
  plus        = "\\+",
  lbracket    = "\\(",
  rbracket    = "\\)",
  newline     = "\n",
  whitespace  = "\\s+"
)

R_code <- "x <- 3 + 4.2 + rnorm(1)"

R_tokens <- lex(R_code, R_patterns)
R_tokens
```

```
##       name whitespace     assign whitespace     number whitespace 
##        "x"        " "       "<-"        " "        "3"        " " 
##       plus whitespace     number whitespace       plus whitespace 
##        "+"        " "      "4.2"        " "        "+"        " " 
##       name   lbracket     number   rbracket 
##    "rnorm"        "("        "1"        ")"
```





