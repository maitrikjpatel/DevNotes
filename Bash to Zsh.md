# Customize Your Shell & Command Prompt

## BASH 

### Good read for Bash files setup
- [Customize your Terminal](http://dobsondev.com/customizing-your-terminal/)
- [Customize Your Shell & Command Prompt](http://blog.taylormcgann.com/2012/06/13/customize-your-shell-command-prompt/)
- [Bash it](https://github.com/Bash-it/bash-it)
### StepsColor Terminal Setup Guide1.	Unzip [Bashfiles.zip](https://www.dropbox.com/s/oe8pi8cqmwoekxe/BashFiles.zip) folder files to your home folder. 2.	Open your finder and enable system files.	- If you have Total-Finder use:⇧⌘.	- Otherwise use following steps: 				* Open Finder		* Open the Utilities folder		* Open a terminal window		* Copy and paste the following line in:				“defaults write com.apple.Finder AppleShowAllFiles YES”		* Press return		* Now hold ‘alt’ on the keyboard and right click on the Finder icon		* Click on Relaunch3.	Make “.bash_files” name folder in your home. It will automatically become hidden. 	- Copy following files in “.bash_files”  folder from unzip folder. 		* .bash_aliases		* .bash_client_helpers		* .bash_exports		* .bash_functions		* .bash_prompt	- Copy remaining two files to home folder 		* .bash_histry 		* .bash_profile 	- You can see the files organized as following picture.  4.	 Now open following three files in your text editor. 		- .bash_prompt , 	- .bash_exports	- .bash_profile	- .bash_prompt  : Please change default_username on line 4. 
					default_username='myname' to default_username='yourname'
	- .bash_exports : Please change export EDITOR on line 2. 				* Textmate Editor users				export EDITOR="/usr/local/bin/mate -w"		* Sublime Editor users 							export EDITOR="/usr/local/bin/subl"	- .bash_profile  : Change file path as following on line 9. 			for file in ~/.bash_files/.	{bash_exports,bash_aliases,bash_functions,bash_prompt,bash_client_helpers}; do5.	Open your terminal and than try the magic. Type bpe and return to open bash files in your terminal. ## Zsh and DotFiles  

### Good read for Bash files setup
 - [GitHub Dotfiles](http://dotfiles.github.io/)
-  [Zero to Hero With Dotfiles](http://code.tutsplus.com/tutorials/setting-up-a-mac-dev-machine-from-zero-to-hero-with-dotfiles--net-35449)
-  [Awesome Dotfiles](https://github.com/webpro/awesome-dotfiles)
-  [Bash to Zsh](http://www.intridea.com/blog/2011/5/18/its-not-enough-to-bash-in-heads-youve-got-to-bash-in-minds-with-zsh)
-  [Oh-My-Zsh](https://github.com/robbyrussell/oh-my-zsh/wiki/Cheatsheet)
-  [Oh-My-Zsh Cheatsheet](https://github.com/robbyrussell/oh-my-zsh/wiki/Cheatsheet)## Command line tuts
[Command Line Crash Course](cli.learncodethehardway.org/book/)## Author- Maitrik Patel || maitrikpatel.com || maitrik1419[at]gmail[dot]com