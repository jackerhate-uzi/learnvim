# Ubuntu 24.02.1 无U盘情况下安装

## 安装准备工作

1. 华硕电脑，系统win11专业版
2. 准备一份7个G左右的空间和Ubuntu安装的空间（100G）
3. 官网下载Ubuntu.X.iso,存放在事先准备好的7GB分区中
4. 安装工具Grub2win,安装完成后点击Manage->Add,选择ISO，改一个容易辨识的名字，点击loading simplify code并edit，内容如下

```grub
clear
set isopath='/ubuntu-24.04.3-desktop-amd64.iso'
set kernelpath='/casper/vmlinuz'
set initrdpath='/casper/initrd'

# 使用 g2wisoboot 函数，它会自动接收设备参数（如 (hd0,gpt4)）并完成启动
g2wisoboot "${isopath}" "${kernelpath}" "${initrdpath}" "boot=casper iso-scan/filename=${isopath} nomodeset noprompt noeject ---"

```

5. 重启，选择文件，即可进入安装，根据提示继续安装即可