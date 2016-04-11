# TODOs

- change all references to gradient themes to
  gradient backgrounds  - why? (avoids confusion with themes as used in other tools)

- change themes.md to gradients.md ? or backgrounds ??

- update samples (from textile to markdown)

- update tutorial (use new text e.g. just markdown; no word about wiki, etc. use write instead of create/author etc.)



## samples to markdown

- fix Slide Show Keyboard Controls (Help) - Action	Key
  - table header (th) gets styles "normal" - should be smaller like td
  - use border and make/add grey-ish background - why? why not?

- rest tables
  - use table first and table second ??  - assign id to slide/div instead of tables - why? why not?

- kramdown footnotes
  - can get placed only at the end of document?
  
- footnotes formatting (make footnotes style smaller - now print in "regular/normal" text size)

- # Universal Identifiers, Formats & Protocols<br>The Holy Trinity
  - can heading use a hard break or allow multi-line text ??

## fix encoding error:

rest.text (on windows)

make sure we always use File.read_utf8( path )

```
  Adding HTML div block for step (incremental display)...

*** error: incompatible character encodings: UTF-8 and IBM437

(erb):118:in `concat': incompatible character encodings: UTF-8 and IBM437 (Encoding::CompatibilityError)
        from (erb):118:in `erb'
```

