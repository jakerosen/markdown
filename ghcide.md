ghcide
  Run version of ghcide that is compiled with the same version of ghc that
  the project is built with
    cabal build -w ghc-8.6.5
    cp dist-newstyle/.../ghcide ~/.local/bin/ghcide-8.6.5

    cabal build -w ghc-8.8.1
    cp dist-newstyle/.../ghcide ~/.local/bin/ghcide-8.8.1


  ghcide-wrapper (plugin calls it)
    if [ ! -z "${GHC_VERSION}" ]; then
      exec ghcide-"${GHC_VERSION}" --lsp
    else
      exit 1
    fi

  :CocConfig (in nvim with plugin)
    {
      "languageserver": {
        "haskell": {
          "command": "ghcide-wrapper",
          "args": [],
          "filetypes": ["haskell", "hs", "lhs"],
          "rootPatterns": ["cabal.project", "stack.yaml"],
          "initializationOptions": {
            "languageServerHaskell": {
            }
          }
        }
      }
    }

  using coc-vim
    gd Go to definition
    ctrl-o jump back

  #Do these every time
    make hie.yaml (in project directory)
    https://github.com/mpickering/hie-bios
    https://github.com/digital-asset/ghcide
      cradle:
        cabal:
          component: "onirim:exe:advent"

    make .envrc
      export GHC_VERSION=8.6.5
