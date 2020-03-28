# aria2 & ariaNG & rclone & caddy 服务安装

[文章地址](https://p3terx.com/archives/offline-download-of-onedrive-gdrive.html)

  ```
    安装aria2
    wget -N https://git.io/aria2.sh && chmod +x aria2.sh && bash aria2.sh
  ```

  rclone
  mount
  ```
  nohup rclone mount Antilochus: /mnt/OneDrive --copy-links --no-gzip-encoding --no-check-certificate --allow-other --allow-non-empty --umask 000 &

  nohup rclone mount Antilochus: /mnt/OneDrive \
  --umask 0000 \
  --default-permissions \
  --allow-non-empty \
  --allow-other \
  --transfers 4 \
  --buffer-size 1024M \
  --low-level-retries 200 \
  --dir-cache-time 12h \
  --vfs-read-chunk-size 32M \
  --vfs-read-chunk-size-limit 1G &

  rclone mount Antilochus: /mnt/OneDrive --allow-other --allow-non-empty --vfs-cache-mode writes
  ```
  [caddy的安装与使用](https://medium.com/@jestem/caddy%E5%AE%98%E6%96%B9%E8%84%9A%E6%9C%AC%E4%B8%80%E9%94%AE%E5%AE%89%E8%A3%85%E4%B8%8E%E4%BD%BF%E7%94%A8-1e6d25154804)
  [安装caddy](https://zorz.cc/post/caddy-filemanager.html)
  [安装ariaNG](https://zorz.cc/post/ubuntu-aria2-ariang.html)
  
  - 出现连接不上aria2时，可能是https配置的问题！rpc
  
  - aria2

  ```
    wget -N https://git.io/aria2.sh && chmod +x aria2.sh && bash aria2.sh
      地址   : 202.182.119.97
      端口   : 6800
      密码   : 7eb25f26a030f650fafa
      目录   : /home/Downloads
  ```

  - rclone
  ```
    rclone 
  ```