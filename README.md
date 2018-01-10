### What is this

See this [ClojureVerse thread](https://clojureverse.org/t/creating-a-central-documentation-repository-website-codox-complications/1287/) 
about a central documentation hub for Clojure similar to Elixir's https://hexdocs.pm/.


You can run what's inside by running

```
boot build-docs --project org.martinklepsch/derivatives --version 0.2.0
```

## Progress

#### HOSTING

- [ ] setup s3 bucket / static website
- [ ] run the build-docs stuff in a container which syncs files to S3 (or similar)

#### GITHUB + NON-API DOCS

- [x] read Github URL from pom.xml or Clojars
- [x] clone repo, copy `doc` directory, provide to codox
- [ ] derive source-uri (probably needs parsing of project.clj or build.boot or perhaps we can derive source locations by overlaying jar contents)
- [ ] figure out what other metadata should be imported
- [ ] Figure out how to deal with changes between tagged releases
  - We probably don't want to pick up API changes since people commonly push development progress straight to `master`
  - Picking up changes to `doc/` would be nice and the above problem probably applies a little less
  - When updating `doc/` triggered by Github commits we need to derive the correct version
    - Take latest "RELEASE" version on Clojars?
    - Take version specified by most recent tag?

#### LONG SHOTS
- [ ] think about discovery of projects with same group-id
- [ ] think about how something like dynadoc (interactive docs) could be integrated
- [ ] think about how grimoire/stack style REPL examples could be integrated

#### BOT

- [ ] notify people that there are api docs available for a jar they just published 
- [ ] nag them to add some plain text documentation/guides