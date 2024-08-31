𝐃𝐨𝐭𝐟𝐢𝐥𝐞𝐬
________________________________________________________________________
𝗚𝗲𝘁𝘁𝗶𝗻𝗴 𝘀𝘁𝗮𝗿𝘁𝗲𝗱 𝗳𝗿𝗼𝗺 𝘀𝗰𝗿𝗮𝘁𝗰𝗵
'''bash
git init --bare $HOME/.cfg
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
config config --local status.showUntrackedFiles no
echo ".cfg" >> $HOME/.gitignore
'''

𝗜𝗺𝗽𝗼𝗿𝘁𝗶𝗻𝗴 𝗼𝘂𝗿 𝗗𝗼𝘁𝗳𝗶𝗹𝗲𝘀 𝗶𝗻𝘁𝗼 𝗮 𝗻𝗲𝘄 𝘀𝘆𝘀𝘁𝗲𝗺

'''bash
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'
echo ".cfg" >> $HOME/.gitignore
git clone --bare git@github.com:ArijitDas2005/Dotfiles.git $HOME/.cfg
config checkout
if [ "$?" -gt 0 ]
then
  mkdir $HOME/.dotfiles.bup
  config checkout 2>&1 | grep "^[[:space:]]" \
    | xargs -I{} mv -v {} $HOME/.dotfiles.bup/{}
fi
config config --local status.showUntrackedFiles no
'''
