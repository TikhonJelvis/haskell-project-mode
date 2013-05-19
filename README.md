This creates a minor mode for Haskell projects.  I loosely define a "Haskell project" as a directory containing a .cabal file.

Currently, the minor mode does two things:

  * Sets the default M-x compile command to build the project using cabal or cabal-dev as appropriate
  * Automatically creates a custom inferior Haskell buffer using cabal-dev ghci for any project using cabal-dev.

I've found both features useful, particularly since I've started using cabal-dev more and more.