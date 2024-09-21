- 👋 Hi, I’m dbgbgtf,or you can just CALL_ME_DBG
- 👀 I’m interested in c,c++,binary exploit,and some python stuff
- 🌱 I’m currently learning python stuff and binary exploit
- 📫 wx:CALL_ME_DBG,qq:88665013

- my .tmux.conf
- ```.conf
  set -g default-terminal "xterm-256color"

  set -g default-shell /bin/zsh

  set -g base-index 1 # 窗口及面板下标起始为1
  set -g pane-base-index 1

  set -g status-interval 60 # 状态栏刷新时间
  set -g status-justify left # 向左对齐

  set -g status-left-length 200 # 状态栏左右长度
  set -g status-right-length 500

  set -g status-style 'bg=color241,fg=color241' # 状态栏整体颜色
  set -g status-right-style 'fg=color159,bg=color234' # 状态栏右侧颜色
  set -g status-left-style 'fg=color159,bg=color234' # 状态栏左侧颜色

  set -g window-status-style 'fg=color208,bg=color233' # 状态栏窗口颜色
  set -g window-status-format " #I#W " # 状态栏窗口显示内容
  set -g window-status-current-style "fg=color235,bg=color184" # 当前状态栏窗口颜色i
  
  set -g status-right " battery:#{echo} #(cat /sys/class/power_supply/BAT1/capacity)% | %A %Y-%m-%d %H:%M"
  set -g status-left "#{echo} #(whoami) "

  set -g window-active-style 'bg=color234' #正在使用的窗口背景色略灰
  set -g window-style 'bg=color232' #窗口背景色为纯黑

  set-option -g pane-active-border-style "bg=color23,fg=color255" # 窗口分割线

  set -g automatic-rename on #窗口重命名等等
  set -g renumber-windows on
  set -g set-titles on
  set -g mouse on

  unbind C-b
  set -g prefix 'C-a'
  bind -n M-Right next-window
  bind -n M-Left previous-window
  
  bind -n M-q new-window #alt+q创建新窗口
  bind -n M-k kill-pane #alt+k杀掉会话
  
  bind -n M-v split-window -h #alt+v 分屏
  bind -n M-c select-pane -L #alt+c 切换窗口
  
  bind r source-file ~/.tmux.conf #ctrl+a r刷新tmux设置
  ```
最终效果，还是挺不错的，没有用到任何tmux之外的插件或是项目
你只需要拥有tmux本体以及256色的终端支持即可(我用的是xterm-256color)
(以及我把ctrl b的前缀改成了ctrl a，这样我在ssh服务器上的终端tmux时就不会把主机和服务器的tmux快捷键混用冲突了)


  ![5f1b82b65bc174dfc16cd231b6a45d35](https://github.com/user-attachments/assets/9b3fbf87-5518-4359-902e-2406a998b2d1)

my .p10k.zsh
```

'builtin' 'local' '-a' 'p10k_config_opts'
[[ ! -o 'aliases'         ]] || p10k_config_opts+=('aliases')
[[ ! -o 'sh_glob'         ]] || p10k_config_opts+=('sh_glob')
[[ ! -o 'no_brace_expand' ]] || p10k_config_opts+=('no_brace_expand')
'builtin' 'setopt' 'no_aliases' 'no_sh_glob' 'brace_expand'

() {
  emulate -L zsh -o extended_glob

  unset -m '(POWERLEVEL9K_*|DEFAULT_USER)~POWERLEVEL9K_GITSTATUS_DIR'

  [[ $ZSH_VERSION == (5.<1->*|<6->.*) ]] || return

  typeset -g POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(
    dir                     
    vcs                     
    newline                 
    prompt_char             
  )

  typeset -g POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(
    status                  
    command_execution_time  
    background_jobs         
    direnv                  
    asdf                    
    virtualenv              
    anaconda                
    pyenv                   
    goenv                   
    nodenv                  
    nvm                     
    nodeenv                 
    rbenv                   
    rvm                     
    fvm                     
    luaenv                  
    jenv                    
    plenv                   
    perlbrew                
    phpenv                  
    scalaenv                
    haskell_stack           
    kubecontext             
    terraform               
    aws                     
    aws_eb_env              
    azure                   
    gcloud                  
    google_app_cred         
    toolbox                 
    context                 
    nordvpn                 
    ranger                  
    yazi                    
    nnn                     
    lf                      
    xplr                    
    vim_shell               
    midnight_commander      
    nix_shell               
    chezmoi_shell           
    todo                    
    timewarrior             
    taskwarrior             
    per_directory_history   
    time                    
    newline
  )

  typeset -g POWERLEVEL9K_MODE=awesome-fontconfig
  typeset -g POWERLEVEL9K_ICON_PADDING=none

  typeset -g POWERLEVEL9K_BACKGROUND=                            
  typeset -g POWERLEVEL9K_{LEFT,RIGHT}_{LEFT,RIGHT}_WHITESPACE=  
  typeset -g POWERLEVEL9K_{LEFT,RIGHT}_SUBSEGMENT_SEPARATOR=' '  
  typeset -g POWERLEVEL9K_{LEFT,RIGHT}_SEGMENT_SEPARATOR=        

  typeset -g POWERLEVEL9K_ICON_BEFORE_CONTENT=true

  typeset -g POWERLEVEL9K_PROMPT_ADD_NEWLINE=true

  typeset -g POWERLEVEL9K_MULTILINE_FIRST_PROMPT_PREFIX='%242F╭─'
  typeset -g POWERLEVEL9K_MULTILINE_NEWLINE_PROMPT_PREFIX='%242F├─'
  typeset -g POWERLEVEL9K_MULTILINE_LAST_PROMPT_PREFIX='%242F╰─'
  typeset -g POWERLEVEL9K_MULTILINE_FIRST_PROMPT_SUFFIX=
  typeset -g POWERLEVEL9K_MULTILINE_NEWLINE_PROMPT_SUFFIX=
  typeset -g POWERLEVEL9K_MULTILINE_LAST_PROMPT_SUFFIX=

  typeset -g POWERLEVEL9K_LEFT_PROMPT_FIRST_SEGMENT_START_SYMBOL='%220F MSI: '
  typeset -g POWERLEVEL9K_RIGHT_PROMPT_LAST_SEGMENT_END_SYMBOL=

  typeset -g POWERLEVEL9K_SHOW_RULER=true
  typeset -g POWERLEVEL9K_RULER_CHAR='─'        
  typeset -g POWERLEVEL9K_RULER_FOREGROUND=243

  typeset -g POWERLEVEL9K_MULTILINE_FIRST_PROMPT_GAP_CHAR=' '
  if [[ $POWERLEVEL9K_MULTILINE_FIRST_PROMPT_GAP_CHAR != ' ' ]]; then
    typeset -g POWERLEVEL9K_MULTILINE_FIRST_PROMPT_GAP_FOREGROUND=242
    typeset -g POWERLEVEL9K_LEFT_PROMPT_LAST_SEGMENT_END_SYMBOL=' '
    typeset -g POWERLEVEL9K_RIGHT_PROMPT_FIRST_SEGMENT_START_SYMBOL=' '
    typeset -g POWERLEVEL9K_EMPTY_LINE_LEFT_PROMPT_FIRST_SEGMENT_END_SYMBOL='%{%}'
    typeset -g POWERLEVEL9K_EMPTY_LINE_RIGHT_PROMPT_FIRST_SEGMENT_START_SYMBOL='%{%}'
  fi

  typeset -g POWERLEVEL9K_OS_ICON_FOREGROUND=

  typeset -g POWERLEVEL9K_PROMPT_CHAR_OK_{VIINS,VICMD,VIVIS,VIOWR}_FOREGROUND=76
  typeset -g POWERLEVEL9K_PROMPT_CHAR_ERROR_{VIINS,VICMD,VIVIS,VIOWR}_FOREGROUND=196
  typeset -g POWERLEVEL9K_PROMPT_CHAR_{OK,ERROR}_VIINS_CONTENT_EXPANSION='❯'
  typeset -g POWERLEVEL9K_PROMPT_CHAR_{OK,ERROR}_VICMD_CONTENT_EXPANSION='❮'
  typeset -g POWERLEVEL9K_PROMPT_CHAR_{OK,ERROR}_VIVIS_CONTENT_EXPANSION='V'
  typeset -g POWERLEVEL9K_PROMPT_CHAR_{OK,ERROR}_VIOWR_CONTENT_EXPANSION='▶'
  typeset -g POWERLEVEL9K_PROMPT_CHAR_OVERWRITE_STATE=true
  typeset -g POWERLEVEL9K_PROMPT_CHAR_LEFT_PROMPT_LAST_SEGMENT_END_SYMBOL=''
  typeset -g POWERLEVEL9K_PROMPT_CHAR_LEFT_PROMPT_FIRST_SEGMENT_START_SYMBOL=

  typeset -g POWERLEVEL9K_DIR_FOREGROUND=45
  typeset -g POWERLEVEL9K_SHORTEN_STRATEGY=truncate_to_unique
  typeset -g POWERLEVEL9K_SHORTEN_DELIMITER=
  typeset -g POWERLEVEL9K_DIR_SHORTENED_FOREGROUND=220
  typeset -g POWERLEVEL9K_DIR_ANCHOR_FOREGROUND=45
  typeset -g POWERLEVEL9K_DIR_ANCHOR_BOLD=true
  local anchor_files=(
    .bzr
    .citc
    .git
    .hg
    .node-version
    .python-version
    .go-version
    .ruby-version
    .lua-version
    .java-version
    .perl-version
    .php-version
    .tool-versions
    .shorten_folder_marker
    .svn
    .terraform
    CVS
    Cargo.toml
    composer.json
    go.mod
    package.json
    stack.yaml
  )
  typeset -g POWERLEVEL9K_SHORTEN_FOLDER_MARKER="(${(j:|:)anchor_files})"
  typeset -g POWERLEVEL9K_DIR_TRUNCATE_BEFORE_MARKER=false
  typeset -g POWERLEVEL9K_SHORTEN_DIR_LENGTH=1
  typeset -g POWERLEVEL9K_DIR_MAX_LENGTH=80
  typeset -g POWERLEVEL9K_DIR_MIN_COMMAND_COLUMNS=40
  typeset -g POWERLEVEL9K_DIR_MIN_COMMAND_COLUMNS_PCT=50
  typeset -g POWERLEVEL9K_DIR_HYPERLINK=false

  typeset -g POWERLEVEL9K_DIR_SHOW_WRITABLE=v3


  typeset -g POWERLEVEL9K_DIR_CLASSES=()


  typeset -g POWERLEVEL9K_VCS_BRANCH_ICON=

  typeset -g POWERLEVEL9K_VCS_UNTRACKED_ICON='?'

  function my_git_formatter() {
    emulate -L zsh

    if [[ -n $P9K_CONTENT ]]; then
      typeset -g my_git_format=$P9K_CONTENT
      return
    fi

    if (( $1 )); then
      local       meta='%f'     
      local      clean='%76F'   
      local   modified='%178F'  
      local  untracked='%39F'   
      local conflicted='%196F'  
    else
      local       meta='%244F'  
      local      clean='%244F'  
      local   modified='%244F'  
      local  untracked='%244F'  
      local conflicted='%244F'  
    fi

    local res

    if [[ -n $VCS_STATUS_LOCAL_BRANCH ]]; then
      local branch=${(V)VCS_STATUS_LOCAL_BRANCH}
      (( $
      res+="${clean}${(g::)POWERLEVEL9K_VCS_BRANCH_ICON}${branch//\%/%%}"
    fi

    if [[ -n $VCS_STATUS_TAG
          && -z $VCS_STATUS_LOCAL_BRANCH  
        ]]; then
      local tag=${(V)VCS_STATUS_TAG}
      (( $
      res+="${meta}
    fi

    [[ -z $VCS_STATUS_LOCAL_BRANCH && -z $VCS_STATUS_TAG ]] &&  
      res+="${meta}@${clean}${VCS_STATUS_COMMIT[1,8]}"

    if [[ -n ${VCS_STATUS_REMOTE_BRANCH:
      res+="${meta}:${clean}${(V)VCS_STATUS_REMOTE_BRANCH//\%/%%}"
    fi

    if [[ $VCS_STATUS_COMMIT_SUMMARY == (|*[^[:alnum:]])(wip|WIP)(|[^[:alnum:]]*) ]]; then
      res+=" ${modified}wip"
    fi

    if (( VCS_STATUS_COMMITS_AHEAD || VCS_STATUS_COMMITS_BEHIND )); then
      (( VCS_STATUS_COMMITS_BEHIND )) && res+=" ${clean}⇣${VCS_STATUS_COMMITS_BEHIND}"
      (( VCS_STATUS_COMMITS_AHEAD && !VCS_STATUS_COMMITS_BEHIND )) && res+=" "
      (( VCS_STATUS_COMMITS_AHEAD  )) && res+="${clean}⇡${VCS_STATUS_COMMITS_AHEAD}"
    elif [[ -n $VCS_STATUS_REMOTE_BRANCH ]]; then
    fi

    (( VCS_STATUS_PUSH_COMMITS_BEHIND )) && res+=" ${clean}⇠${VCS_STATUS_PUSH_COMMITS_BEHIND}"
    (( VCS_STATUS_PUSH_COMMITS_AHEAD && !VCS_STATUS_PUSH_COMMITS_BEHIND )) && res+=" "
    (( VCS_STATUS_PUSH_COMMITS_AHEAD  )) && res+="${clean}⇢${VCS_STATUS_PUSH_COMMITS_AHEAD}"
    (( VCS_STATUS_STASHES        )) && res+=" ${clean}*${VCS_STATUS_STASHES}"
    [[ -n $VCS_STATUS_ACTION     ]] && res+=" ${conflicted}${VCS_STATUS_ACTION}"
    (( VCS_STATUS_NUM_CONFLICTED )) && res+=" ${conflicted}~${VCS_STATUS_NUM_CONFLICTED}"
    (( VCS_STATUS_NUM_STAGED     )) && res+=" ${modified}+${VCS_STATUS_NUM_STAGED}"
    (( VCS_STATUS_NUM_UNSTAGED   )) && res+=" ${modified}!${VCS_STATUS_NUM_UNSTAGED}"
    (( VCS_STATUS_NUM_UNTRACKED  )) && res+=" ${untracked}${(g::)POWERLEVEL9K_VCS_UNTRACKED_ICON}${VCS_STATUS_NUM_UNTRACKED}"
    (( VCS_STATUS_HAS_UNSTAGED == -1 )) && res+=" ${modified}─"

    typeset -g my_git_format=$res
  }
  functions -M my_git_formatter 2>/dev/null

  typeset -g POWERLEVEL9K_VCS_MAX_INDEX_SIZE_DIRTY=-1

  typeset -g POWERLEVEL9K_VCS_DISABLED_WORKDIR_PATTERN='~'

  typeset -g POWERLEVEL9K_VCS_DISABLE_GITSTATUS_FORMATTING=true
  typeset -g POWERLEVEL9K_VCS_CONTENT_EXPANSION='${$((my_git_formatter(1)))+${my_git_format}}'
  typeset -g POWERLEVEL9K_VCS_LOADING_CONTENT_EXPANSION='${$((my_git_formatter(0)))+${my_git_format}}'
  typeset -g POWERLEVEL9K_VCS_{STAGED,UNSTAGED,UNTRACKED,CONFLICTED,COMMITS_AHEAD,COMMITS_BEHIND}_MAX_NUM=-1

  typeset -g POWERLEVEL9K_VCS_VISUAL_IDENTIFIER_COLOR=76
  typeset -g POWERLEVEL9K_VCS_LOADING_VISUAL_IDENTIFIER_COLOR=244
  typeset -g POWERLEVEL9K_VCS_VISUAL_IDENTIFIER_EXPANSION=

  typeset -g POWERLEVEL9K_VCS_BACKENDS=(git)

  typeset -g POWERLEVEL9K_VCS_CLEAN_FOREGROUND=76
  typeset -g POWERLEVEL9K_VCS_UNTRACKED_FOREGROUND=76
  typeset -g POWERLEVEL9K_VCS_MODIFIED_FOREGROUND=178

  typeset -g POWERLEVEL9K_STATUS_EXTENDED_STATES=true

  typeset -g POWERLEVEL9K_STATUS_OK=false
  typeset -g POWERLEVEL9K_STATUS_OK_FOREGROUND=70
  typeset -g POWERLEVEL9K_STATUS_OK_VISUAL_IDENTIFIER_EXPANSION='✔'

  typeset -g POWERLEVEL9K_STATUS_OK_PIPE=true
  typeset -g POWERLEVEL9K_STATUS_OK_PIPE_FOREGROUND=70
  typeset -g POWERLEVEL9K_STATUS_OK_PIPE_VISUAL_IDENTIFIER_EXPANSION='✔'

  typeset -g POWERLEVEL9K_STATUS_ERROR=false
  typeset -g POWERLEVEL9K_STATUS_ERROR_FOREGROUND=160
  typeset -g POWERLEVEL9K_STATUS_ERROR_VISUAL_IDENTIFIER_EXPANSION='✘'

  typeset -g POWERLEVEL9K_STATUS_ERROR_SIGNAL=true
  typeset -g POWERLEVEL9K_STATUS_ERROR_SIGNAL_FOREGROUND=160
  typeset -g POWERLEVEL9K_STATUS_VERBOSE_SIGNAME=false
  typeset -g POWERLEVEL9K_STATUS_ERROR_SIGNAL_VISUAL_IDENTIFIER_EXPANSION='✘'

  typeset -g POWERLEVEL9K_STATUS_ERROR_PIPE=true
  typeset -g POWERLEVEL9K_STATUS_ERROR_PIPE_FOREGROUND=160
  typeset -g POWERLEVEL9K_STATUS_ERROR_PIPE_VISUAL_IDENTIFIER_EXPANSION='✘'

  typeset -g POWERLEVEL9K_COMMAND_EXECUTION_TIME_THRESHOLD=3
  typeset -g POWERLEVEL9K_COMMAND_EXECUTION_TIME_PRECISION=0
  typeset -g POWERLEVEL9K_COMMAND_EXECUTION_TIME_FOREGROUND=224
  typeset -g POWERLEVEL9K_COMMAND_EXECUTION_TIME_FORMAT='d h m s'
  typeset -g POWERLEVEL9K_COMMAND_EXECUTION_TIME_VISUAL_IDENTIFIER_EXPANSION=

  typeset -g POWERLEVEL9K_BACKGROUND_JOBS_VERBOSE=false
  typeset -g POWERLEVEL9K_BACKGROUND_JOBS_FOREGROUND=70

  typeset -g POWERLEVEL9K_DIRENV_FOREGROUND=178

  typeset -g POWERLEVEL9K_ASDF_FOREGROUND=66


  typeset -g POWERLEVEL9K_ASDF_SOURCES=(shell local global)

  typeset -g POWERLEVEL9K_ASDF_PROMPT_ALWAYS_SHOW=false

  typeset -g POWERLEVEL9K_ASDF_SHOW_SYSTEM=true

  typeset -g POWERLEVEL9K_ASDF_SHOW_ON_UPGLOB=

  typeset -g POWERLEVEL9K_ASDF_RUBY_FOREGROUND=168

  typeset -g POWERLEVEL9K_ASDF_PYTHON_FOREGROUND=37

  typeset -g POWERLEVEL9K_ASDF_GOLANG_FOREGROUND=37

  typeset -g POWERLEVEL9K_ASDF_NODEJS_FOREGROUND=70

  typeset -g POWERLEVEL9K_ASDF_RUST_FOREGROUND=37

  typeset -g POWERLEVEL9K_ASDF_DOTNET_CORE_FOREGROUND=134

  typeset -g POWERLEVEL9K_ASDF_FLUTTER_FOREGROUND=38

  typeset -g POWERLEVEL9K_ASDF_LUA_FOREGROUND=32

  typeset -g POWERLEVEL9K_ASDF_JAVA_FOREGROUND=32

  typeset -g POWERLEVEL9K_ASDF_PERL_FOREGROUND=67

  typeset -g POWERLEVEL9K_ASDF_ERLANG_FOREGROUND=125

  typeset -g POWERLEVEL9K_ASDF_ELIXIR_FOREGROUND=129

  typeset -g POWERLEVEL9K_ASDF_POSTGRES_FOREGROUND=31

  typeset -g POWERLEVEL9K_ASDF_PHP_FOREGROUND=99

  typeset -g POWERLEVEL9K_ASDF_HASKELL_FOREGROUND=172

  typeset -g POWERLEVEL9K_ASDF_JULIA_FOREGROUND=70

  typeset -g POWERLEVEL9K_NORDVPN_FOREGROUND=39
  typeset -g POWERLEVEL9K_NORDVPN_{DISCONNECTED,CONNECTING,DISCONNECTING}_CONTENT_EXPANSION=
  typeset -g POWERLEVEL9K_NORDVPN_{DISCONNECTED,CONNECTING,DISCONNECTING}_VISUAL_IDENTIFIER_EXPANSION=

  typeset -g POWERLEVEL9K_RANGER_FOREGROUND=178
  
  typeset -g POWERLEVEL9K_YAZI_FOREGROUND=178

  typeset -g POWERLEVEL9K_NNN_FOREGROUND=72

  typeset -g POWERLEVEL9K_LF_FOREGROUND=72

  typeset -g POWERLEVEL9K_XPLR_FOREGROUND=72

  typeset -g POWERLEVEL9K_VIM_SHELL_FOREGROUND=34

  typeset -g POWERLEVEL9K_MIDNIGHT_COMMANDER_FOREGROUND=178

  typeset -g POWERLEVEL9K_NIX_SHELL_FOREGROUND=74




  typeset -g POWERLEVEL9K_CHEZMOI_SHELL_FOREGROUND=33

  typeset -g POWERLEVEL9K_DISK_USAGE_NORMAL_FOREGROUND=35
  typeset -g POWERLEVEL9K_DISK_USAGE_WARNING_FOREGROUND=220
  typeset -g POWERLEVEL9K_DISK_USAGE_CRITICAL_FOREGROUND=160
  typeset -g POWERLEVEL9K_DISK_USAGE_WARNING_LEVEL=90
  typeset -g POWERLEVEL9K_DISK_USAGE_CRITICAL_LEVEL=95
  typeset -g POWERLEVEL9K_DISK_USAGE_ONLY_WARNING=false

  typeset -g POWERLEVEL9K_RAM_FOREGROUND=66

  typeset -g POWERLEVEL9K_SWAP_FOREGROUND=96

  typeset -g POWERLEVEL9K_LOAD_WHICH=5
  typeset -g POWERLEVEL9K_LOAD_NORMAL_FOREGROUND=66
  typeset -g POWERLEVEL9K_LOAD_WARNING_FOREGROUND=178
  typeset -g POWERLEVEL9K_LOAD_CRITICAL_FOREGROUND=166

  typeset -g POWERLEVEL9K_TODO_FOREGROUND=110
  typeset -g POWERLEVEL9K_TODO_HIDE_ZERO_TOTAL=true
  typeset -g POWERLEVEL9K_TODO_HIDE_ZERO_FILTERED=false



  typeset -g POWERLEVEL9K_TIMEWARRIOR_FOREGROUND=224
  typeset -g POWERLEVEL9K_TIMEWARRIOR_CONTENT_EXPANSION='${P9K_CONTENT:0:24}${${P9K_CONTENT:24}:+…}'


  typeset -g POWERLEVEL9K_TASKWARRIOR_FOREGROUND=226



  typeset -g POWERLEVEL9K_PER_DIRECTORY_HISTORY_LOCAL_FOREGROUND=135
  typeset -g POWERLEVEL9K_PER_DIRECTORY_HISTORY_GLOBAL_FOREGROUND=130



  typeset -g POWERLEVEL9K_CPU_ARCH_FOREGROUND=172



  typeset -g POWERLEVEL9K_CONTEXT_ROOT_FOREGROUND=176
  typeset -g POWERLEVEL9K_CONTEXT_{REMOTE,REMOTE_SUDO}_FOREGROUND=180
  typeset -g POWERLEVEL9K_CONTEXT_FOREGROUND=180

  typeset -g POWERLEVEL9K_CONTEXT_ROOT_TEMPLATE='%B%n@%m'
  typeset -g POWERLEVEL9K_CONTEXT_{REMOTE,REMOTE_SUDO}_TEMPLATE='%n@%m'
  typeset -g POWERLEVEL9K_CONTEXT_TEMPLATE='%n@%m'

  typeset -g POWERLEVEL9K_CONTEXT_{DEFAULT,SUDO}_{CONTENT,VISUAL_IDENTIFIER}_EXPANSION=


  typeset -g POWERLEVEL9K_VIRTUALENV_FOREGROUND=37
  typeset -g POWERLEVEL9K_VIRTUALENV_SHOW_PYTHON_VERSION=false
  typeset -g POWERLEVEL9K_VIRTUALENV_SHOW_WITH_PYENV=false
  typeset -g POWERLEVEL9K_VIRTUALENV_{LEFT,RIGHT}_DELIMITER=
  typeset -g POWERLEVEL9K_VIRTUALENV_VISUAL_IDENTIFIER_EXPANSION='🐍'

  typeset -g POWERLEVEL9K_ANACONDA_FOREGROUND=37

  typeset -g POWERLEVEL9K_ANACONDA_CONTENT_EXPANSION='${${${${CONDA_PROMPT_MODIFIER

  typeset -g POWERLEVEL9K_ANACONDA_VISUAL_IDENTIFIER_EXPANSION='🐍'

  typeset -g POWERLEVEL9K_PYENV_FOREGROUND=37
  typeset -g POWERLEVEL9K_PYENV_SOURCES=(shell local global)
  typeset -g POWERLEVEL9K_PYENV_PROMPT_ALWAYS_SHOW=false
  typeset -g POWERLEVEL9K_PYENV_SHOW_SYSTEM=true

  typeset -g POWERLEVEL9K_PYENV_CONTENT_EXPANSION='${P9K_CONTENT}${${P9K_CONTENT:

  typeset -g POWERLEVEL9K_PYENV_VISUAL_IDENTIFIER_EXPANSION='🐍'

  typeset -g POWERLEVEL9K_GOENV_FOREGROUND=37
  typeset -g POWERLEVEL9K_GOENV_SOURCES=(shell local global)
  typeset -g POWERLEVEL9K_GOENV_PROMPT_ALWAYS_SHOW=false
  typeset -g POWERLEVEL9K_GOENV_SHOW_SYSTEM=true

  typeset -g POWERLEVEL9K_NODENV_FOREGROUND=70
  typeset -g POWERLEVEL9K_NODENV_SOURCES=(shell local global)
  typeset -g POWERLEVEL9K_NODENV_PROMPT_ALWAYS_SHOW=false
  typeset -g POWERLEVEL9K_NODENV_SHOW_SYSTEM=true

  typeset -g POWERLEVEL9K_NVM_FOREGROUND=70
  typeset -g POWERLEVEL9K_NVM_PROMPT_ALWAYS_SHOW=false
  typeset -g POWERLEVEL9K_NVM_SHOW_SYSTEM=true

  typeset -g POWERLEVEL9K_NODEENV_FOREGROUND=70
  typeset -g POWERLEVEL9K_NODEENV_SHOW_NODE_VERSION=false
  typeset -g POWERLEVEL9K_NODEENV_{LEFT,RIGHT}_DELIMITER=

  typeset -g POWERLEVEL9K_NODE_VERSION_FOREGROUND=70
  typeset -g POWERLEVEL9K_NODE_VERSION_PROJECT_ONLY=true

  typeset -g POWERLEVEL9K_GO_VERSION_FOREGROUND=37
  typeset -g POWERLEVEL9K_GO_VERSION_PROJECT_ONLY=true

  typeset -g POWERLEVEL9K_RUST_VERSION_FOREGROUND=37
  typeset -g POWERLEVEL9K_RUST_VERSION_PROJECT_ONLY=true

  typeset -g POWERLEVEL9K_DOTNET_VERSION_FOREGROUND=134
  typeset -g POWERLEVEL9K_DOTNET_VERSION_PROJECT_ONLY=true

  typeset -g POWERLEVEL9K_PHP_VERSION_FOREGROUND=99
  typeset -g POWERLEVEL9K_PHP_VERSION_PROJECT_ONLY=true

  typeset -g POWERLEVEL9K_LARAVEL_VERSION_FOREGROUND=161

  typeset -g POWERLEVEL9K_JAVA_VERSION_FOREGROUND=32
  typeset -g POWERLEVEL9K_JAVA_VERSION_PROJECT_ONLY=true
  typeset -g POWERLEVEL9K_JAVA_VERSION_FULL=false

  typeset -g POWERLEVEL9K_PACKAGE_FOREGROUND=117

  typeset -g POWERLEVEL9K_RBENV_FOREGROUND=168
  typeset -g POWERLEVEL9K_RBENV_SOURCES=(shell local global)
  typeset -g POWERLEVEL9K_RBENV_PROMPT_ALWAYS_SHOW=false
  typeset -g POWERLEVEL9K_RBENV_SHOW_SYSTEM=true

  typeset -g POWERLEVEL9K_RVM_FOREGROUND=168
  typeset -g POWERLEVEL9K_RVM_SHOW_GEMSET=false
  typeset -g POWERLEVEL9K_RVM_SHOW_PREFIX=false

  typeset -g POWERLEVEL9K_FVM_FOREGROUND=38

  typeset -g POWERLEVEL9K_LUAENV_FOREGROUND=32
  typeset -g POWERLEVEL9K_LUAENV_SOURCES=(shell local global)
  typeset -g POWERLEVEL9K_LUAENV_PROMPT_ALWAYS_SHOW=false
  typeset -g POWERLEVEL9K_LUAENV_SHOW_SYSTEM=true

  typeset -g POWERLEVEL9K_JENV_FOREGROUND=32
  typeset -g POWERLEVEL9K_JENV_SOURCES=(shell local global)
  typeset -g POWERLEVEL9K_JENV_PROMPT_ALWAYS_SHOW=false
  typeset -g POWERLEVEL9K_JENV_SHOW_SYSTEM=true

  typeset -g POWERLEVEL9K_PLENV_FOREGROUND=67
  typeset -g POWERLEVEL9K_PLENV_SOURCES=(shell local global)
  typeset -g POWERLEVEL9K_PLENV_PROMPT_ALWAYS_SHOW=false
  typeset -g POWERLEVEL9K_PLENV_SHOW_SYSTEM=true

  typeset -g POWERLEVEL9K_PERLBREW_FOREGROUND=67
  typeset -g POWERLEVEL9K_PERLBREW_PROJECT_ONLY=true
  typeset -g POWERLEVEL9K_PERLBREW_SHOW_PREFIX=false

  typeset -g POWERLEVEL9K_PHPENV_FOREGROUND=99
  typeset -g POWERLEVEL9K_PHPENV_SOURCES=(shell local global)
  typeset -g POWERLEVEL9K_PHPENV_PROMPT_ALWAYS_SHOW=false
  typeset -g POWERLEVEL9K_PHPENV_SHOW_SYSTEM=true

  typeset -g POWERLEVEL9K_SCALAENV_FOREGROUND=160
  typeset -g POWERLEVEL9K_SCALAENV_SOURCES=(shell local global)
  typeset -g POWERLEVEL9K_SCALAENV_PROMPT_ALWAYS_SHOW=false
  typeset -g POWERLEVEL9K_SCALAENV_SHOW_SYSTEM=true

  typeset -g POWERLEVEL9K_HASKELL_STACK_FOREGROUND=172
  typeset -g POWERLEVEL9K_HASKELL_STACK_SOURCES=(shell local)
  typeset -g POWERLEVEL9K_HASKELL_STACK_ALWAYS_SHOW=true

  typeset -g POWERLEVEL9K_KUBECONTEXT_SHOW_ON_COMMAND='kubectl|helm|kubens|kubectx|oc|istioctl|kogito|k9s|helmfile|flux|fluxctl|stern|kubeseal|skaffold|kubent|kubecolor|cmctl|sparkctl'

  typeset -g POWERLEVEL9K_KUBECONTEXT_CLASSES=(
      '*'       DEFAULT)
  typeset -g POWERLEVEL9K_KUBECONTEXT_DEFAULT_FOREGROUND=134

  typeset -g POWERLEVEL9K_KUBECONTEXT_DEFAULT_CONTENT_EXPANSION=
  POWERLEVEL9K_KUBECONTEXT_DEFAULT_CONTENT_EXPANSION+='${P9K_KUBECONTEXT_CLOUD_CLUSTER:-${P9K_KUBECONTEXT_NAME}}'
  POWERLEVEL9K_KUBECONTEXT_DEFAULT_CONTENT_EXPANSION+='${${:-/$P9K_KUBECONTEXT_NAMESPACE}:


  typeset -g POWERLEVEL9K_TERRAFORM_SHOW_DEFAULT=false
  typeset -g POWERLEVEL9K_TERRAFORM_CLASSES=(
      '*'         OTHER)
  typeset -g POWERLEVEL9K_TERRAFORM_OTHER_FOREGROUND=38

  typeset -g POWERLEVEL9K_TERRAFORM_VERSION_FOREGROUND=38

  typeset -g POWERLEVEL9K_AWS_SHOW_ON_COMMAND='aws|awless|cdk|terraform|pulumi|terragrunt'

  typeset -g POWERLEVEL9K_AWS_CLASSES=(
      '*'       DEFAULT)
  typeset -g POWERLEVEL9K_AWS_DEFAULT_FOREGROUND=208

  typeset -g POWERLEVEL9K_AWS_CONTENT_EXPANSION='${P9K_AWS_PROFILE//\%/%%}${P9K_AWS_REGION:+ ${P9K_AWS_REGION//\%/%%}}'

  typeset -g POWERLEVEL9K_AWS_EB_ENV_FOREGROUND=70

  typeset -g POWERLEVEL9K_AZURE_SHOW_ON_COMMAND='az|terraform|pulumi|terragrunt'

  typeset -g POWERLEVEL9K_AZURE_CLASSES=(
      '*'         OTHER)

  typeset -g POWERLEVEL9K_AZURE_OTHER_FOREGROUND=32

  typeset -g POWERLEVEL9K_GCLOUD_SHOW_ON_COMMAND='gcloud|gcs|gsutil'
  typeset -g POWERLEVEL9K_GCLOUD_FOREGROUND=32

  typeset -g POWERLEVEL9K_GCLOUD_PARTIAL_CONTENT_EXPANSION='${P9K_GCLOUD_PROJECT_ID//\%/%%}'
  typeset -g POWERLEVEL9K_GCLOUD_COMPLETE_CONTENT_EXPANSION='${P9K_GCLOUD_PROJECT_NAME//\%/%%}'

  typeset -g POWERLEVEL9K_GCLOUD_REFRESH_PROJECT_NAME_SECONDS=60


  typeset -g POWERLEVEL9K_GOOGLE_APP_CRED_SHOW_ON_COMMAND='terraform|pulumi|terragrunt'

  typeset -g POWERLEVEL9K_GOOGLE_APP_CRED_CLASSES=(
      '*'             DEFAULT)
  typeset -g POWERLEVEL9K_GOOGLE_APP_CRED_DEFAULT_FOREGROUND=32

  typeset -g POWERLEVEL9K_GOOGLE_APP_CRED_DEFAULT_CONTENT_EXPANSION='${P9K_GOOGLE_APP_CRED_PROJECT_ID//\%/%%}'

  typeset -g POWERLEVEL9K_TOOLBOX_FOREGROUND=178
  typeset -g POWERLEVEL9K_TOOLBOX_CONTENT_EXPANSION='${P9K_TOOLBOX_NAME:

  typeset -g POWERLEVEL9K_PUBLIC_IP_FOREGROUND=94

  typeset -g POWERLEVEL9K_VPN_IP_FOREGROUND=81
  typeset -g POWERLEVEL9K_VPN_IP_CONTENT_EXPANSION=
  typeset -g POWERLEVEL9K_VPN_IP_INTERFACE='(gpd|wg|(.*tun)|tailscale)[0-9]*|(zt.*)'
  typeset -g POWERLEVEL9K_VPN_IP_SHOW_ALL=false

  typeset -g POWERLEVEL9K_IP_FOREGROUND=38
  typeset -g POWERLEVEL9K_IP_CONTENT_EXPANSION='$P9K_IP_IP${P9K_IP_RX_RATE:+ %70F⇣$P9K_IP_RX_RATE}${P9K_IP_TX_RATE:+ %215F⇡$P9K_IP_TX_RATE}'
  typeset -g POWERLEVEL9K_IP_INTERFACE='[ew].*'

  typeset -g POWERLEVEL9K_PROXY_FOREGROUND=68

  typeset -g POWERLEVEL9K_BATTERY_LOW_THRESHOLD=20
  typeset -g POWERLEVEL9K_BATTERY_LOW_FOREGROUND=160
  typeset -g POWERLEVEL9K_BATTERY_{CHARGING,CHARGED}_FOREGROUND=70
  typeset -g POWERLEVEL9K_BATTERY_DISCONNECTED_FOREGROUND=178
  typeset -g POWERLEVEL9K_BATTERY_STAGES=('%K{232}▁' '%K{232}▂' '%K{232}▃' '%K{232}▄' '%K{232}▅' '%K{232}▆' '%K{232}▇' '%K{232}█')
  typeset -g POWERLEVEL9K_BATTERY_VERBOSE=false

  typeset -g POWERLEVEL9K_WIFI_FOREGROUND=68


  typeset -g POWERLEVEL9K_TIME_FOREGROUND=224
  typeset -g POWERLEVEL9K_TIME_FORMAT='%D{%H:%M:%S}'
  typeset -g POWERLEVEL9K_TIME_UPDATE_ON_COMMAND=false
  typeset -g POWERLEVEL9K_TIME_VISUAL_IDENTIFIER_EXPANSION=

  function prompt_example() {
    p10k segment -f 208 -i '⭐' -t 'hello, %n'
  }

  function instant_prompt_example() {
    prompt_example
  }


  typeset -g POWERLEVEL9K_TRANSIENT_PROMPT=always

  typeset -g POWERLEVEL9K_INSTANT_PROMPT=verbose

  typeset -g POWERLEVEL9K_DISABLE_HOT_RELOAD=true

  (( ! $+functions[p10k] )) || p10k reload
}

typeset -g POWERLEVEL9K_CONFIG_FILE=${${(%):-%x}:a}

(( ${
'builtin' 'unset' 'p10k_config_opts'
```


