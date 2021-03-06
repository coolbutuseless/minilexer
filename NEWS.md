NEWS
============

v0.1.7 2018-09-29
------------------

* Disallow multiple captured groups in a single pattern
    * Because a single call to `string_match_all()` is used to perform the lex, 
      multiple captured groups within a pattern won't work. Added a check to
      explicitly disallow this sort of pattern.

v0.1.6 2018-08-26
------------------

* Removed `TokenStream`. Use `ministreamer::NamedValueStream` package instead.

v0.1.5 2018-08-12
------------------

* Added a hack for `consume_until_names()`. Not at all optimized.

v0.1.4 2018-04-22
------------------

* fixed a missing 'drop=FALSE' bug

v0.1.3 2018-03-30
------------------

* `TokenStream` changes
    * `consume_tokens_of_type()` as a way to consume multiple tokens of a specified type
    * the `type` and `value` arguments can now be scalars or vectors in order to do more complex token matching
    * More tests
    

v0.1.2 2018-03-29
------------------

* Add a `debug` argument to `lex()`


v0.1.1 2018-03-27
------------------

* Added documentation for `TokenStream`
* Added some simple tests


v0.1.0 2018-03-27
------------------

* Initial release
