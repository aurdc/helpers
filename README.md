# helpers
This content is derived from the [ArchWiki](https://wiki.archlinux.org) **AUR helpers** article, in particular the revision as of [14:08, 1 October 2018](https://wiki.archlinux.org/index.php?title=AUR_helpers&oldid=545420).

## Legend

The columns have the following meaning:

<dl>
<dt>File review</dt>
<dd>Does not source the <tt>PKGBUILD</tt> at all by default; or, alerts the user and offers the opportunity to inspect the PKGBUILD manually before it is sourced. Some helpers are known to source PKGBUILDs before the user can inspect them, <b>allowing malicious code to be executed</b>. <i>Optional</i> means that there is a command line flag or configuration option to prevent the automatic sourcing before viewing.</dd>

<dt>Diff view</dt>
<dd>Ability to view package differences on inspection. Besides the <tt>PKGBUILD</tt>, this includes changes to files such as <tt>.install</tt> or <tt>.patch</tt> files.</dd>

<dt>Git clone</dt>
<dd>Uses <a href="https://jlk.fjfi.cvut.cz/arch/manpages/man/extra/git/git-clone.1.en">git clone(1)</a> by default to retrieve build files from the AUR.</dd>

<dt>Reliable parser</dt> 
<dd>Ability to handle complex packages by using the provided metadata (RPC/.SRCINFO) instead of PKGBUILD <a  href="https://en.wikipedia.org/wiki/Parsing#Parser">parsing</a>, such as <a href="https://aur.archlinux.org/packages/aws-cli-git/">aws-cli-git</a>.</dd>

<dt>Reliable solver</dt> 
<dd>Ability to correctly solve and build complex dependency chains, such as <a href="https://aur.archlinux.org/packages/ros-lunar-desktop/">ros-lunar-desktop</a>.</dd>

<dt>Split packages</dt>
<dd>Ability to correctly build and install:</dd>
<dd>Multiple packages from the same package base, without rebuilding or reinstalling multiple times, such as <a href="https://aur.archlinux.org/packages/clion">clion</a>.</dd>
<dd>Split packages which depend on a package from the same package base, such as <a href="https://aur.archlinux.org/packages/libc++">libc++</a> and <a href="https://aur.archlinux.org/packages/libc++abi">libc++abi</a>.</dd>
<dd>Split packages independently, such as <a href="https://aur.archlinux.org/packages/python-pyalsaaudio">python-pyalsaaudio</a> and <a href="https://aur.archlinux.org/packages/python2-pyalsaaudio">python2-pyalsaaudio</a>.</dd>

<dt>Clean build</dt>
<dd>Does not export new variables that can prevent a successful build process.</dd>

<dt>Batch interaction</dt>
<dd>Ability to prompt before the build process, in particular:</dd>
<dd>Inspection of package files or their differences</dd>
<dd>Summary of package upgrades;</dd>
<dd>Resolution of package conflicts and installations.</dd>
<dd>An asterisk denotes functionality specifically enabled by the user.</dd>

<dt>Shell completion</dt>
<dd><a href="https://en.wikipedia.org/wiki/Command-line_completion">Tab completion</a> is available for the listed <i>shells</i>.</dd>
</dl>

----
#### Note

* Table rows are sorted by column values, where Yes or N/A take precedence over Partial or Optional and No, or alphabetically if values are equal.

* Optional means that a feature is available, but only through a command-line argument or configuration option. Partial means that a feature is not fully implemented, or that it partially deviates from the given criteria.
----

## Search and download

| Name                                    | Written in | File review        | Git clone          | Reliable parser                                                                  | Reliable solver    | Shell completion | Specificity                             |
| ---                                     | ---        | ---                | ---                | ---                                                                              | ---                | ---              | ---                                     |
| pbget                                   | Python     | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark:                                                               | –                  | –                |                                         |
| yaah                                    | Bash       | :heavy_check_mark: | :warning:          | :heavy_check_mark:                                                               | –                  | –                |                                         |
| auracle-git                             | C++        | :heavy_check_mark: | :no_entry:         | :heavy_check_mark:                                                               | :heavy_check_mark: | –                | print build order                       |
| cower                                   | C          | :heavy_check_mark: | :no_entry:         | :heavy_check_mark:                                                               | –                  | –                | regex support, sort by votes/popularity |
| package-query                           | C          | :heavy_check_mark: | –                  | :no_entry: [1](https://github.com/archlinuxfr/package-query/issues/135)          | –                  | –                | search only                             |
| repoctl                                 | Go         | :heavy_check_mark: | :no_entry:         | :heavy_check_mark: [2](https://github.com/goulash/pacman/blob/master/aur/aur.go) | –                  | –                | local repository support                |
| aurel <br><small>(discontinued)</small> | Emacs Lisp | :heavy_check_mark: | :no_entry:         | :heavy_check_mark:                                                               | –                  | –                | Emacs integration                       |
