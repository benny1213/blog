#  shadowsocksr服务端安装
  [文章链接](https://ssr.tools/31)
  ```
  获取安装脚本
  wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh

  修改脚本权限
  chmod +x shadowsocks-all.sh

  启动脚本
  ./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log

  另一个脚本：
  wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh

  ```