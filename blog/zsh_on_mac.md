# zsh 在 mac 上的配置
创建时间：2026年 4月23日 星期四 11时20分34秒 CST<br>
修改时间：2026年 4月23日 星期四 11时20分34秒 CST<br>

mac 上的 zsh 自带了一些配置，所以与 Linux 配置不同。<br>
- 删除历史记录配置，mac自带。
- 添加fpath，不是标准目录。
```shell
fpath+=(/opt/homebrew/share/zsh/site-functions)
# The following lines were added by compinstall
zstyle :compinstall filename '/Users/fia/.zshrc'
autoload -Uz compinit
compinit
# End of lines added by compinstall

alias ls='ls --color=auto'
alias grep='grep --color=auto'

source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh
eval "$(starship init zsh)"
```