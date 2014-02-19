# Haskell Project Mode

This creates a minor mode for managing Haskell projects. I loosely define a "Haskell project" as any directory containing a .cabal file.

Currently, the minor mode does two things:

  * Sets the default M-x compile command to build the project using cabal or cabal-dev as appropriate
  * Automatically creates a custom inferior Haskell buffer using cabal-dev ghci for projects using cabal-dev or cabal repl for projects using cabal sandboxes.
  * Automatically create another custom inferior Haskell buffer for your tests if you're using cabal sandboxes. This assumes your test suite is named `test` and calls `cabal repl test` which loads your test suite's dependencies and packages. 

It currently automatically identifies directories that use cabal-dev or cabal sandboxes. If you're using both for whatever unholy reason, it'll default to cabal-dev. (Or maybe it'll just break—I haven't test this!)

I've found both features useful, particularly since I've started using cabal-dev (and now cabal sandboxes) more and more.

Note: with `cabal-dev`, you have to run `cabal-dev configure` or `cabal-dev install` before using GHCi in a brand new project.

## Installation

First, put `haskell-project-mode.el` into your load-path. Then put all the shell scripts (`ghci-dev`, `ghci-sandbox` and `ghci-test`) into your path somewhere. Require the mode:

    (require 'haskell-project-mode)

Finally, to automatically enable the mode for all Haskell files, add this to your `.emacs`:

    (add-hook 'haskell-mode-hook 'haskell-project-mode)
    
If inferior GHCi buffers are not working properly, adding the following might help:

    (setq inferior-haskell-find-project-root nil)
