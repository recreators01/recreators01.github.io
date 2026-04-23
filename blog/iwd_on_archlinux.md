# iwd 在arch上使用遇到的问题
创建时间：2026年 03月 04日 星期三 12:12:33 CST<br>
修改时间：2026年 03月 04日 星期三 21:36:13 CST<br>

## iwd 与 openresolv 搭配使用的问题
```
iwd[1664]: /usr/lib/resolvconf/libc: line 259: /etc/resolv.conf: Read-only file system
```
解决方案：
1. 修改openresolv配置
    ```
    resolv_conf=/run/resolvconf/resolv.conf
    ```
    将 /etc/resolv.conf 符号链接到 /run/resolvconf/resolv.conf
   
1. [参考 archwiki 扩展 iwd.service systemd 单元](https://wiki.archlinux.org/title/Iwd#/etc/resolv.conf:%20Read-only%20file%20system:~:text=IPv4%5D%0ASendHostname%3Dtrue-,/etc/resolv.conf%3A%20Read%2Donly%20file%20system,-When%20using%20resolvconf)

## 使用 iwd 内置DHCP在多AP网络下的问题
在多AP网络环境下使用iwd内置dhcp会导致连接时间过长，原因是iwd一直在漫游。由于iwd将获取ip状态视为未连接，iwd在此时仍会进行漫游，直到找到最好的一个连接。<br>

解决方案：使用 dhcpcd 管理获取 ip, iwd 直接连接不会获得漫游的等待时间。