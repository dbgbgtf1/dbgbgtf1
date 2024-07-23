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

