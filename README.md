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
  
  set -g status-style 'bg=color243,fg=color11' # 状态栏整体颜色
  set -g status-right-style 'fg=color172,bg=color232' # 状态栏右侧颜色
  set -g status-left-style 'fg=color36,bg=color255' # 状态栏左侧颜色
  set -g window-status-style 'fg=color208,bg=color232' # 状态栏窗口颜色
  set -g window-status-format " #I  #W  " # 状态栏窗口显示内容
  set -g window-status-current-style "fg=color235,bg=color214" # 当前状态栏窗口颜色i
  set -g status-right "#{echo} #(cat /sys/class/power_supply/BAT1/capacity)% | %A %Y-%m-%d %H:%M" # 状态栏右侧显示内容
  set -g status-left "#{echo} #(whoami)@#{=20:pane_title} " # 状态栏左侧显示内容
  
  set -g automatic-rename on # 重命名
  set -g renumber-windows on
  set -g set-titles on
  
  set -g mouse on # 鼠标功能启用
  set -g prefix2 C-a # ctrl b作为前缀键
  
  unbind '"' # unbind一些我不需要的东西
  unbind '%'
  unbind C-b
  
  bind r source-file ~/.tmux.conf # 用来快速测试.conf文件效果
  ```
最终效果，还是挺不错的，没有用到任何tmux之外的插件或是项目
你只需要拥有tmux本体以及256色的终端支持即可(我用的是xterm-256color)
![image](https://github.com/dbgbgtf1/dbgbgtf1/assets/149954065/776029ac-46ec-4771-8dbb-01bd5f3b79ef)

  
