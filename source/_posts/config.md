---
title: 各种配置
catalog: true
comments: true
date: 2022-04-13 17:52:54
header-img: snail-bg.jpg
tags:
  - json
categories:
  - config

---

## prettier config

```json
module.exports = {
  printWidth: 120, // 每行代码长度（默认80）
  tabWidth: 2, // 每个tab相当于多少个空格（默认2）
  useTabs: false, // 是否使用tab进行缩进（默认false）
  singleQuote: true, // 使用单引号（默认false）
  semi: false, // 声明结尾使用分号(默认true)
  htmlWhitespaceSensitivity: 'ignore',
  trailingComma: 'none', // 多行使用拖尾逗号（默认none）
  bracketSpacing: true, // 对象字面量的大括号间使用空格（默认true）
  jsxBracketSameLine: true, // 多行JSX中的>放置在最后一行的结尾，而不是另起一行（默认false）
  arrowParens: 'always' // 只有一个参数的箭头函数的参数是否带圆括号（默认avoid）
}
```

## vscode config

```json
{
    "editor.tabSize": 2,
    // #每次保存的时候将代码按eslint格式进行修复
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    //  #让函数(名)和后面的括号之间加个空格
    "javascript.format.insertSpaceBeforeFunctionParenthesis": true,
    // #这个按用户自身习惯选择 
    "vetur.format.defaultFormatter.html": "js-beautify-html",
    "vetur.format.defaultFormatterOptions": {
        "js-beautify-html": {
            "wrap_attributes": "force-aligned"
            // #vue组件中html代码格式化样式
        }
    },
    "workbench.iconTheme": "vscode-icons-mac",
    "terminal.integrated.profiles.osx": {
        "zsh": {
            "path": "zsh"
        }
    },
    "editor.fontSize": 14,
    "git.ignoreLimitWarning": true,
    "debug.javascript.usePreview": false,
    "javascript.updateImportsOnFileMove.enabled": "always",
    "[vue]": {
        "editor.defaultFormatter": "octref.vetur"
    },
    "prettier.semi": false,
    "prettier.singleQuote": true,
    "prettier.tabWidth": 2,
    "vetur.format.defaultFormatter.js": "vscode-typescript",
    // "[javascript]": {
    //     "editor.defaultFormatter": "esbenp.prettier-vscode"
    // },
    "[typescript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "workbench.editorAssociations": {
        "*": "default"
    },
    "window.zoomLevel": 2,
    "leetcode.endpoint": "leetcode-cn",
    "leetcode.workspaceFolder": "/Volumes/HDD/力扣题目",
    "terminal.integrated.env.osx": {
        "FIG_NEW_SESSION": "1"
    },
    "editor.accessibilitySupport": "off",
    "[javascript]": {
        "editor.defaultFormatter": "vscode.typescript-language-features"
    },
    "prettier.printWidth": 120,
    "[html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "diffEditor.ignoreTrimWhitespace": false,
    "workbench.editor.splitInGroupLayout": "vertical",
    "vetur.validation.script": false,
    "editor.formatOnPaste": true,
    "editor.formatOnSave": true,
    "leetcode.hint.commentDescription": false,
  }
```

## zshrc config

```shell
# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
export ZSH="$HOME/.oh-my-zsh"

# Set name of the theme to load --- if set to "random", it will
# load a random theme each time oh-my-zsh is loaded, in which case,
# to know which specific one was loaded, run: echo $RANDOM_THEME
# See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
ZSH_THEME="robbyrussell"

# Set list of themes to pick from when loading at random
# Setting this variable when ZSH_THEME=random will cause zsh to load
# a theme from this variable instead of looking in $ZSH/themes/
# If set to an empty array, this variable will have no effect.
# ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" )

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion.
# Case-sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment one of the following lines to change the auto-update behavior
# zstyle ':omz:update' mode disabled  # disable automatic updates
# zstyle ':omz:update' mode auto      # update automatically without asking
# zstyle ':omz:update' mode reminder  # just remind me to update when it's time

# Uncomment the following line to change how often to auto-update (in days).
# zstyle ':omz:update' frequency 13

# Uncomment the following line if pasting URLs and other text is messed up.
# DISABLE_MAGIC_FUNCTIONS="true"

# Uncomment the following line to disable colors in ls.
# DISABLE_LS_COLORS="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
# ENABLE_CORRECTION="true"

# Uncomment the following line to display red dots whilst waiting for completion.
# You can also set it to another string to have that shown instead of the default red dots.
# e.g. COMPLETION_WAITING_DOTS="%F{yellow}waiting...%f"
# Caution: this setting can cause issues with multiline prompts in zsh < 5.7.1 (see #5765)
# COMPLETION_WAITING_DOTS="true"

# Uncomment the following line if you want to disable marking untracked files
# under VCS as dirty. This makes repository status check for large repositories
# much, much faster.
# DISABLE_UNTRACKED_FILES_DIRTY="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# You can set one of the optional three formats:
# "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# or set a custom format using the strftime function format specifications,
# see 'man strftime' for details.
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load?
# Standard plugins can be found in $ZSH/plugins/
# Custom plugins may be added to $ZSH_CUSTOM/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(git zsh-autosuggestions)

source $ZSH/oh-my-zsh.sh

# User configuration

# export MANPATH="/usr/local/man:$MANPATH"

# You may need to manually set your language environment
# export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
# if [[ -n $SSH_CONNECTION ]]; then
#   export EDITOR='vim'
# else
#   export EDITOR='mvim'
# fi

# Compilation flags
# export ARCHFLAGS="-arch x86_64"

# Set personal aliases, overriding those provided by oh-my-zsh libs,
# plugins, and themes. Aliases can be placed here, though oh-my-zsh
# users are encouraged to define aliases within the ZSH_CUSTOM folder.
# For a full list of active aliases, run `alias`.
#
# Example aliases
# alias zshconfig="mate ~/.zshrc"
# alias ohmyzsh="mate ~/.oh-my-zsh"

# 自定义别名
alias yd="yarn dev"
alias yda="yarn dev:api"
alias yb="yarn build"
alias ybw="yarn build-watch"
alias code="/Applications/Visual\ Studio\ Code.app/Contents/Resources/app/bin/code"
alias subl="/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl"
alias ng="sudo nginx"
alias ngt="sudo nginx -t"
alias ngsr="sudo nginx -s reload"
alias ngst="sudo nginx -s stop"

# oh my zsh 扩展命令
alias gstat="git add . && git stash save '暂存' && git stash apply stash@{0} && git restore --staged ."
alias glgf="git log --stat --date=format:'%Y年%m月%d日%H时%M分%S秒'"
alias gdap="gb -D release/prod && git push origin --delete release/prod && gcm && gl && gcb release/prod"
alias gdat="gb -D release/test && git push origin --delete release/test && gcm && gcb release/test"
alias gallm="gm feature/sg-refactor && gm feature/sg-refactor-server && gm feature/server-common && gm feature/server-bankcard && gm feature/sg-refactor-client && gm feature/client-bankcard-list"
alias gstam="git stash save '暂存'"

# 自定义环境变量
export NODE_ENV='development'

# 加上时间戳
RPROMPT="%D %T %"

# autojump插件
[[ -s `brew --prefix`/etc/autojump.sh ]] && . `brew --prefix`/etc/autojump.sh

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm

# chrome别名
alias chrome="/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome"
```