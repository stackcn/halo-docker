# Halo [ˈheɪloʊ]
> Halo 是一款现代化的个人独立博客系统，给习惯写博客的同学多一个选择。
> [官网](https://halo.run)

## Docker 安装
> 自行查阅 [官方文档](https://docs.docker.com/engine/install/)

## Docker-compose 安装
> [官方文档](https://docs.docker.com/compose/install/)

## Dokcer-compose 一键部署

```
 # git clone https://github.com/stackcn/halo-docker
 # cd halo-docker
 # docker-compose -d up 
```

### nginx 配置
> Nginx 配置文件 nginx/sites/default (默认配置)
> 可以自己添加网站格式如 example_com.conf
```
 server {
        listen 80;
        # listen 443 ssl;
        # ssl_certificate /etc/nginx/ssl/cert-file-name.pem;  #需要将cert-file-name.pem替换成已上传的证书文件的名称。
        # ssl_certificate_key /etc/nginx/ssl/cert-file-name.key; #需要将cert-file-name.key替换成已上传的证书密钥文件的名称。
        # ssl_session_timeout 5m;
        # ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
    
        # 开启 ssl 证书后 打开 http 跳转 https
        # if ( $scheme = http ){
        # return      301 https://$server_name$request_uri;
        # }


        # 表示使用的加密套件的类型。
        # ssl_protocols TLSv1 TLSv1.1 TLSv1.2; #表示使用的TLS协议的类型。
        # ssl_prefer_server_ciphers on;

       

        # root /var/www/html;
        server_name 127.0.0.1;  # 127.0.0.1 替换为自己的域名

        index index.html index.htm index.nginx-debian.html;
        location / {
                client_max_body_size    1000m;
                proxy_set_header        Host    $http_host;
                proxy_redirect off;
                proxy_pass http://halo:8090;
                proxy_http_version 1.1;
        }
}
```
> 如果 需要开启ssl证书，申请自己的证书后 按照配置文件替换修改


打开 127.0.0.1 进入安装界面

