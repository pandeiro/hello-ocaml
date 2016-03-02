# hello-ocaml
Explorations of the OCaml programming language

Based mostly on [Real World OCaml](https://realworldocaml.org/) and
the
[Beginner's Guide to OCaml beginners guides](http://blog.nullspace.io/beginners-guide-to-ocaml-beginners-guides.html),

## Installation on Arch

#### Get OCaml from extra:

```
$ sudo pacman -S ocaml
```

#### Download OPAM via binary (AUR version was broken for me):

```
$ wget https://raw.github.com/ocaml/opam/master/shell/opam_installer.sh -O - | sh -s /usr/local/bin
```

Run init again so you can answer "yes" to the .profile question:

```
$ opam init
```

#### Get utop

```
$ opam install utop
```

#### Install editor tooling

Install merlin:

```
$ opam install merlin
```

Install tuareg for Emacs:

- Add `(depends-on "tuareg")` to `~/.emacs.d/Cask`

Install ocp-indent for Emacs:

- Add `(depends-on "ocp-indent")` to `~/.emacs.d/Cask`

Finally, add this is Emacs config:

```elisp
(setq opam-share (substring (shell-command-to-string "opam config var share 2> /dev/null") 0 -1))
(add-to-list 'load-path (concat opam-share "/emacs/site-lisp"))
(require 'merlin)
(add-hook 'tuareg-mode-hook 'merlin-mode t)
(add-hook 'caml-mode-hook 'merlin-mode t)
(setq merlin-use-auto-complete-mode 'easy)
(setq merlin-command 'opam)
```

