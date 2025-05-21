1.编辑添加相关源，可参考目前本人使用

/etc/opkg.conf

dest root /
dest ram /tmp
lists_dir ext /var/opkg-lists
option overlay_root /overlay

arch all 1
arch noarch 1
arch aarch64_cortex-a53 5
arch aarch64_cortex-a53_neon-vfpv4 10



/etc/opkg/customfeeds.conf


# add your custom package feeds here
#
# src/gz example_feed_name http://www.example.com/path/to/files

src/gz base https://mirrors.aliyun.com/openwrt/releases/23.05-SNAPSHOT/packages/aarch64_cortex-a53/base
src/gz packages https://mirrors.aliyun.com/openwrt/releases/23.05-SNAPSHOT/packages/aarch64_cortex-a53/packages
src/gz routing https://mirrors.aliyun.com/openwrt/releases/23.05-SNAPSHOT/packages/aarch64_cortex-a53/routing
src/gz luci https://mirrors.aliyun.com/openwrt/releases/23.05-SNAPSHOT/packages/aarch64_cortex-a53/luci
src/gz openwrt_base https://mirrors.pku.edu.cn/openwrt/releases/23.05.5/packages/aarch64_cortex-a53/base/
src/gz openwrt_luci https://mirrors.pku.edu.cn/openwrt/releases/23.05.5/packages/aarch64_cortex-a53/luci
src/gz openwrt_packages https://mirrors.pku.edu.cn/openwrt/releases/23.05.5/packages/aarch64_cortex-a53/packages
src/gz openwrt_routing https://mirrors.pku.edu.cn/openwrt/releases/23.05.5/packages/aarch64_cortex-a53/routing
src/gz openwrt_telephony https://mirrors.pku.edu.cn/openwrt/releases/23.05.5/packages/aarch64_cortex-a53/telephony
src/gz cooluc https://opkg.cooluc.com/openwrt-23.05/aarch64_cortex-a53/



/etc/opkg/distfeeds.conf

src/gz glinet_core https://fw.gl-inet.cn/releases/v23.05-SNAPSHOT/kmod-5.4.164/aarch64_cortex-a53_neon-vfpv4/ipq60xx
src/gz opnwrt_packages https://fw.gl-inet.cn/releases/v23.05-SNAPSHOT/packages-5.0/aarch64_cortex-a53_neon-vfpv4/packages


2.更新opkg源
opkg update


3.下载clash安装包并安装
wget wget -O /tmp/openclash.ipk https://github.com/vernesong/OpenClash/releases/download/v0.46.079/luci-app-openclash_0.46.079_all.ipk
opkg install /tmp/openclash.ipk
rm -f /tmp/openclash.ipk

4.退出登录重新进入luci界面，不出意外应该就会有服务选项-openclash，如果没有参考以下链接安装依赖试试

https://github.com/vernesong/OpenClash/releases
