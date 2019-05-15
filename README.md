# linux 配置phpMyAdmin

**官网**
> https://www.phpmyadmin.net/

**下载phpMyAdmin**
```
wget install https://files.phpmyadmin.net/phpMyAdmin/4.8.5/phpMyAdmin-4.8.5-all-languages.zip
```
> wget Linux 下载工具   
> wget [参数] [URL地址]

**安装phpMyAdmin**
```
unzip phpMyAdmin-4.8.5-all-languages.zip
```

**查看nginx配置路径**
```
cd /etc/nginx/conf.d
```

**配置**
```
sudo nano localhost-php-myadmin.conf

 1 server {
 2  server_name 域名;
 3  root myAdmin的路径;
 4  index index.php;
 5
 6  location ~ \.php$ {
 7   fastcgi_pass  127.0.0.1:9000;#这个端口号是php-fpm的端口，默认为9000
10   fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
11   include fastcgi_params;
12  }
13 }
```

**重启nginx**
```
sudo service nginx reload
```