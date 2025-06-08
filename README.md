# Tmpstpdwn's Auto-Rice Bootstrapping Scripts (TARBS)

## What is TARBS?

TARBS is a script that autoinstalls and autoconfigures a fully-functioning
and minimal void Linux environment.

## Customization

I manage dotfiles using [The git bare method](https://www.atlassian.com/git/tutorials/dotfiles).
Therefore this script installs dotfiles using the method described in that article.

The list of packages to be installed and folders to be created are stored in the dotfiles at `$HOME/.packages` &&
`$HOME/.folders`.
This works as the package installations and folder setup happens after dofiles installation.

By default, TARBS installs [my dotfiles repo (voidrice) here](https://github.com/tmpstpdwn/.dotfiles).
so the list of packages it uses is [here in .packages](https://github.com/tmpstpdwn/.dotfiles/blob/main/.packages) and
list of folders it uses is [here in .folders](https://github.com/tmpstpdwn/.dotfiles/blob/main/.folders).

You can change this behaviour by modifying the `dotfilesrepo` variable in the script to make it use your dotfiles
repo.

### The `.packages` list

TARBS will parse the given programs list and install all given programs. Note
that the programs file must be a three column `.csv`.

The first column is a "tag" that determines how the program is installed, ""
(blank) for the main repository or `G` if the program is a
git repository that is meant to be `make && sudo make install`ed.

The second column is the name of the program in the repository, or the link to
the git repository, and the third column is a description (should be a verb
phrase) that describes the program. During installation, TARBS will print out
this information in a grammatical sentence. It also doubles as documentation
for people who read the CSV and want to install my dotfiles manually.

Depending on your own build, you may want to tactically order the programs in
your programs file. TARBS will install from the top to the bottom.

If you include commas in your program descriptions, be sure to include double
quotes around the whole description to ensure correct parsing.

### The script itself

The script is extensively divided into functions for easier readability and
trouble-shooting. Most everything should be self-explanatory.

The main work is done by the `installationloop` function, which iterates
through the programs file and determines based on the tag of each program,
which commands to run to install it. You can easily add new methods of
installations and tags as well.

## LICENSE

This project is licensed under GPL3 [LICENSE](LICENSE).
