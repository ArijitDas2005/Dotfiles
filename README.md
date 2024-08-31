Dotfiles
Getting started from scratch

git init --bare $HOME/.cfg
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
config config --local status.showUntrackedFiles no
echo ".cfg" >> $HOME/.gitignore

Importing our Dotfiles into a new system

alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
echo ".cfg" >> $HOME/.gitignore
git clone --bare git@github.com:Mike184Kilic/Dotfiles.git $HOME/.cfg
config checkout
if [ "$?" -gt 0 ]
then
  mkdir $HOME/.dotfiles.bup
  config checkout 2>&1 | grep "^[[:space:]]" \
    | xargs -I{} mv -v {} $HOME/.dotfiles.bup/{}
fi
config config --local status.showUntrackedFiles no
