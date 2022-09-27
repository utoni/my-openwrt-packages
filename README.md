HowTo use this repository as OpenWrt feed
=========================================

```shell
git clone https://github.com/utoni/my-openwrt-packages.git ./my-openwrt-packages
git clone https://github.com/openwrt/openwrt.git ./openwrt
cd openwrt
sed -i "1s,^,src-link my_openwrt_packages $(realpath ../my-openwrt-packages)\n," ./feeds.conf
make distclean
./scripts/feeds update -a && ./scripts/feeds install -a
make menuconfig
```

If you change `my_openwrt_packages` to something else, you need to change the include path in
`lang/rust/rustc_environment.mk` to `include $(TOPDIR)/package/feeds/[your-feed-name]/rust/rustc_targets.mk`.
Otherwise, `rust/host` will not be able to compile as well as packages that depend on Rust (e.g. `suricata6`).

Why?
====

This feeds contains packages that are:

 * rejected by upstream
 * in development and not ready for upstream
 * outdated/archived and will never be seen in upstream

Packages
========

 * btop: https://github.com/aristocratos/btop
 * rust: https://github.com/Itus-Shield/packages/tree/rust
 * rust_host: https://github.com/Itus-Shield/packages/tree/rust_host
 * libndpi: https://github.com/ntop/nDPI/commits/master
 * td: https://github.com/tdlib/td
 * nDPId: https://github.com/utoni/nDPId
 * nDPId-master: https://github.com/utoni/nDPId/commits/main
 * shadowsocks-libev: https://github.com/shadowsocks/shadowsocks-libev/commits/master
 * suricata6: https://github.com/Itus-Shield/packages/tree/suricata6
 * suricata-update: https://github.com/Itus-Shield/packages/tree/suricata6
 * tools: https://github.com/utoni/tools/commits/master
