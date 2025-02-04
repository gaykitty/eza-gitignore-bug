# Eza gitignore Bug Example

This bug was observed on eza v0.20.18

How to reproduce:

```
git clone --recurse-submodules https://github.com/gaykitty/eza-gitignore-bug.git
cd eza-gitignore-bug/eza-gitignore-bug-sub-project
cargo b
cd ..
eza -TR --git-ignore
```

The following will be printed despite the fact that the target directory is ignored in the git
submodule:

```
 .
├──  eza-gitignore-bug-sub-project
│   ├──  src
│   │   └──  lib.rs
│   ├──  target
│   │   ├──  debug
│   │   │   ├──  build
│   │   │   ├──  deps
│   │   │   │   ├──  eza_gitignore_bug_sub_project-f1a7d4631a632f40.d
│   │   │   │   ├──  libeza_gitignore_bug_sub_project-f1a7d4631a632f40.rlib
│   │   │   │   └──  libeza_gitignore_bug_sub_project-f1a7d4631a632f40.rmeta
│   │   │   ├──  examples
│   │   │   ├──  incremental
│   │   │   │   └──  eza_gitignore_bug_sub_project-0n7mxfiebkyiz
│   │   │   │       ├──  s-h4ajwx0qqb-1kcrkwh-d8u2911jnh99lzx42qeja5q3o
│   │   │   │       │   ├──  ahbz54rrlszqvjvhyibck1tag.o
│   │   │   │       │   ├──  dep-graph.bin
│   │   │   │       │   ├──  query-cache.bin
│   │   │   │       │   └──  work-products.bin
│   │   │   │       └──  s-h4ajwx0qqb-1kcrkwh.lock
│   │   │   ├──  libeza_gitignore_bug_sub_project.d
│   │   │   └──  libeza_gitignore_bug_sub_project.rlib
│   │   └──  CACHEDIR.TAG
│   ├──  Cargo.lock
│   └──  Cargo.toml
└──  package.json
```
