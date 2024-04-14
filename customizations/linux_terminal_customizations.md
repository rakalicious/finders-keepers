
How to Make Linux Terminal look Awesome
In this article, we will install and configure some themes and plugins to tweak our Linux terminal for better productivity and a fancier look. These features include autocompletion, autosuggestion, command-line search, syntax highlighting, and better support for git and environment managers.

## Zsh

The Z-shell or Zsh is a UNIX shell with support for various plugins and themes.

sudo apt install zsh      [ Debian/Ubuntu ]
sudo yum install zsh      [ RedHat/CentOS ]
sudo pacman -S zsh        [ Arch/Manjaro ]
sudo dnf install zsh      [ Fedora ]
sudo zypper install zsh   [ OpenSUSE ]

![](https://media.geeksforgeeks.org/wp-content/uploads/20220527181900/1.png)

## Oh My Zsh 

It is an open-source and community-driven framework for managing Zsh configuration. It comes bundled with thousands of helpful functions,  plugins, themes, and much more.

> sh -c “$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)” [Using curl]
> 
> sh -c “$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)”   [Using wget]

![](https://media.geeksforgeeks.org/wp-content/uploads/20220527182227/2.png)

## Nerd Fonts 

Nerd Fonts is a project to create patched fonts. Nerd Fonts takes popular programming fonts and patches them with a large number of glyphs (icons).

-   Download [hack](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/Hack/Regular/complete/Hack%20Regular%20Nerd%20Font%20Complete.ttf) font and install it by double-clicking on the .tff file. You can also use any other font but make sure it supports all the icons and glyphs required by powerlevel10k.
-   Select **Hack Font** as the default font.

![](https://media.geeksforgeeks.org/wp-content/uploads/20220527182546/3.png)

## Powerlevel10k 

Powerlevel10k is a theme for Zsh.  It changes normal shell commands to colorful commands and emphasizes speed, flexibility, and out-of-the-box experience.

> git clone –depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k

![](https://media.geeksforgeeks.org/wp-content/uploads/20220527182707/1.gif)

-   An installation prompt will begin by default, but if it doesn’t run.

$ p10k configure

-   Change the default theme to ZSH_THEME=”powerlevel10k/powerlevel10k” inside ~/.zshrc.
-   Commit the changes by running 

$ source ~/.zshr

![](https://media.geeksforgeeks.org/wp-content/uploads/20220527182728/21.gif)

## zsh-autosuggestions 

Real-time type-ahead completion for Zsh. Asynchronous find-as-you-type autocompletion.

> git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

-   Add zsh-autocomplete to the list of plugins inside ~/.zshrc plugins=( [plugins…])
-   Commit the changes by running source ~/.zshrc

![](https://media.geeksforgeeks.org/wp-content/uploads/20220527182757/3.gif)

## zsh-syntaxhighlighting

zsh-syntax-highlighting provides syntax highlighting for the shell zsh. It enables highlighting commands whilst they are typed at a zsh prompt into an interactive terminal. This helps review commands before running them, particularly in catching syntax errors.

> git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

-   Add zsh-syntax-highlighting to the list of plugins inside ~/.zshrc plugins=( [plugins…])
-   Commit the changes by running source ~/.zshrc

![](https://media.geeksforgeeks.org/wp-content/uploads/20220527182820/4.gif)

## diff-so-fancy

It is a tool that converts the output of diff utility into a more human-readable form. It improves the development speed by providing a simpler way to compare recent changes. With diff-so-fancy, one can focus on the code quality instead of figuring out what all the + and – mean?

$ npm i -g diff-so-fancy

![](https://media.geeksforgeeks.org/wp-content/uploads/20220602165456/ter1.png)

To integrate diff-so-fancy with git.

> $ git config –global core.pager “diff-so-fancy | less –tabs=4 -RFX”
> 
> $ git config –global interactive.diffFilter “diff-so-fancy –patch”
> 
> $ git config –global color.ui true

![](https://media.geeksforgeeks.org/wp-content/uploads/20220602165456/ter2.png)

Now, we can simply use the git diff command to view recent changes.

$ git diff

![](https://media.geeksforgeeks.org/wp-content/uploads/20220602165455/ter3.png)

## bat

bat is a supercharged version of the native cat command. It includes features like syntax highlighting, git integration, automatic paging, and much more.

sudo apt install bat      [ Debian/Ubuntu ]
sudo yum install bat      [ RedHat/CentOS ]
sudo pacman -S bat        [ Arch/Manjaro ]
sudo dnf install bat      [ Fedora ]
sudo zypper install bat   [Image Widget OpenSUSE ]

Viewing the content of a file with first cat and then with bat.

![](https://media.geeksforgeeks.org/wp-content/uploads/20220602165455/ter4.png)

![](https://media.geeksforgeeks.org/wp-content/uploads/20220602165454/ter6.png)

![](https://media.geeksforgeeks.org/wp-content/uploads/20220602165453/ter7.png)

![](https://media.geeksforgeeks.org/wp-content/uploads/20220602165452/ter8.png)

## fzf 

It’s an interactive Unix filter for command-line that can be used with any list; files, command history, processes, hostnames, bookmarks, git commits, etc.

> $ git clone –depth 1 https://github.com/junegunn/fzf.git ~/.fzf
> 
> $ ~/.fzf/install

![](https://media.geeksforgeeks.org/wp-content/uploads/20220527182927/5.gif)

-   ctrl + t to navigate through the file system.

![](https://media.geeksforgeeks.org/wp-content/uploads/20220527182941/6.gif)

yehd

-   ctrl + r to navigate through older commands.

![](https://media.geeksforgeeks.org/wp-content/uploads/20220527182957/7.gif)
