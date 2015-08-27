git branch --merged master | grep -v master$ | xargs -n 1 git branch -d

ps auxw | grep rails
kill -9 4664 (first id #)

g       = 'git'
gst     = 'git status'
gd      = 'git diff'
gdc     = 'git diff --cached'
gl      = 'git pull'

gb      = 'git branch'

glg     = 'git log --stat --max-count=10'
glgg    = 'git log --graph --max-count=10'
glgga   = 'git log --graph --decorate --all'
glo     = 'git log --oneline'

alias gco='git checkout'
alias gst='git status'
alias gci='git commit'
alias gl='git pull'
alias glg='git log --date-order --all --graph --format="%C(green)%h%Creset %C(yellow)%an%Creset %C(blue bold)%ar%Creset %C(red bold)%d%Creset%s"'
alias gcm='git checkout master'

# grep with color
alias grep='grep --color=auto'

# postgres
alias pgdown='pg_ctl -D /usr/local/var/postgres stop -s -m fast'
alias pgup= pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log start

pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log start
