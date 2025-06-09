# Tmpstpdwn's Auto-Rice Bootstrapping Scripts (TARBS)

## What is TARBS?

TARBS is a script that autoinstalls and autoconfigures a minimal Linux environment.

## What does it do?

TARBS does the following things:
- Download and setup dotfiles.
- install packages.

I manage dotfiles using [The git bare method](https://www.atlassian.com/git/tutorials/dotfiles).
Therefore this script installs dotfiles using the method described in the article.

TARBS require `.packages` csv file,  a list of packages to be installed, mode of installation and a short desciption for each package.
This file is expected to be at `$HOME/.packages` of the dotfiles git repo.

As the packages are installed after dotfiles setup, putting the package list in the dotfiles git repo makes it convenient.

## Customization

By default, TARBS installs [my dotfiles repo (voidrice) here](https://github.com/tmpstpdwn/.dotfiles).
so the list of packages it uses is [here in .packages](https://github.com/tmpstpdwn/.dotfiles/blob/main/.packages).

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
this information in a grammatical sentence.

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
