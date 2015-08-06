### OS X Setup
* set password
* clear Dock
* sync Calendar

### Apps from App Store
* flycut
* Slack

### Apps from the Web
* iTerm
* Sublime Text 3
	* `ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl” /usr/local/bin/subl`
* ShiftIt
* Chrome
* vagrant
* virtualbox
* mou
* spiff (GH release -> /usr/local/bin)
* cf (GH release -> /usr/local/bin)
* homebrew
* git bash completions
* fly (from concourse CI)
* veritas

### Programs from `brew`
* `brew install awscli caskroom/cask/brew-cask direnv dos2unix fluid gdbm \
				go htop-osx jq libffi libyaml mysql ncdu openssl postgresql \
				readline ruby-install tree watch wget`
* With `ruby-install` you can then `ruby-install ruby x.x.x`
* With `fluid` you can then make the Tracker app

### `~/.bash_profile`
```
## GOLANG ##
export GOPATH=~/.gopaths/go-1.4.2
export PATH=$GOPATH/bin/:$PATH

## RUBY ##
export PATH=~/.rubies/ruby-2.1.6/bin/:$PATH

## BOSH ##
alias bosh="BUNDLE_GEMFILE=~/.bosh.Gemfile bundle exec bosh"

## GIT ##
if [ -f ~/.git-completion.bash ]; then
  . ~/.git-completion.bash
fi

## DIRENV ##
eval "$(direnv hook bash)"

## WORKSPACE ##
alias forex='for x in `ls ~/workspace`; do (echo $x; cd ~/workspace/$x; git st); done'

## EDITOR ##
export EDITOR=subl
export GIT_EDITOR=vim

[[ -s ~/.bashrc ]] && source ~/.bashrc
```

### Ruby Gems
* `gem install bundler`
* `echo "source 'https://rubygems.org'; gem 'bosh_cli'" > ~/.bosh.Gemfile && BUNDLE_GEMFILE=~/.bosh.Gemfile bundle`
* `echo "gem: --no-document" > ~/.gemrc`

### SSH
* add work key to `~/.ssh` and `ssh-add` it to the keychain

### `~/.gitconfig`
```
[user]
	name = <YOUR NAME HERE>
	email = <YOUR EMAIL HERE>
[push]
	default = simple
[url "git@github.com:"]
	pushInsteadOf = "https://github.com/"
[alias]
	plog = log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
	st = status
	co = checkout
	ci = commit
	ps = push --recurse-submodules=check
```