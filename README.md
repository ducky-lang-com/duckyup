# duckyup

Install and update scripts for **[Ducky](https://github.com/ducky-lang-com/ducky-lang)**
— the small, statically typed language that compiles to native x86-64
machine code.

`install.sh` and `update.sh` in this repository are mirrors of the scripts
at the root of the canonical
[ducky-lang](https://github.com/ducky-lang-com/ducky-lang) repository, so
either location serves the same files. The one-liners below read from the
main repository:

```sh
# install the latest Ducky release (compiler + updater + extension)
curl -fsSL https://raw.githubusercontent.com/ducky-lang-com/ducky-lang/main/install.sh | sh

# update an existing installation in place
curl -fsSL https://raw.githubusercontent.com/ducky-lang-com/ducky-lang/main/update.sh | sh
```

## What the scripts do

**`install.sh`**

* builds `duckyc` from source and installs it (default `~/.local/bin`,
  `--prefix DIR` to override, `--user` for the user prefix);
* installs the `ducky-update` command and the `share/ducky-lang` data;
* installs the **Ducky** extension for VS Code / VSCodium / Cursor
  (`--no-editor` to skip, `--uninstall` to remove everything);
* removes files installed under the pre-rename names (`duckc`,
  `duck-update`, `share/duck-lang`, `duck-lang-*`), so upgrading from
  Duck v0.6 or earlier does not leave two compilers on `PATH`.

**`update.sh`** (installed as `ducky-update`)

* from a git checkout: `git pull --ff-only` and reinstalls your local
  sources — local work is never overwritten;
* anywhere else, including `curl | sh`: downloads the latest sources into
  a temporary directory, builds and installs them;
* `--check` only reports whether a newer version exists;
* forwards `--user`, `--prefix DIR` and `--no-editor` to `install.sh`.

## Releases

Prebuilt, statically linked binaries ship with every release of the main
repository: <https://github.com/ducky-lang-com/ducky-lang/releases>
(`duckyc-linux-x86_64` since v0.7.0).

Documentation, source and the issue tracker all live in
[ducky-lang](https://github.com/ducky-lang-com/ducky-lang).
