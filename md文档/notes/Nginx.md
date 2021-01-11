# Nginx

## Ubuntu 安装

https://blog.csdn.net/qq_31461919/article/details/106468937



### 常用命令

```
nginx -v

cd /etc/nginx/

nginx -c /etc/nginx/nginx.conf    //启动nginx

http://10.0.1.234:3080/

sudo lsof -i:3080
sudo netstat -anp | grep 3080   查询监听进程

/usr/sbin/nginx -s reload            # 重新载入配置文件
/usr/sbin/nginx -s reopen            # 重启 Nginx
/usr/sbin/nginx -s stop              # 停止 Nginx
/usr/sbin/nginx -t		#验证是否正确
```



### Nginx下配置Https证书详细过程

https://blog.csdn.net/smartdt/article/details/80027579



谷歌问题

https://blog.csdn.net/zhangxingyu126/article/details/105010443?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param



配置

```
#user  nobody;
worker_processes  1;

error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;

#pid        logs/nginx.pid;


events {
    worker_connections  1024;
}


http {
    include       mime.types;
    default_type  application/octet-stream;

    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    #access_log  logs/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    keepalive_timeout  65;

    #gzip  on;
    #设置允许发布内容为8M
    client_max_body_size 100M;
    client_body_buffer_size 128k;

    server {
        listen       3000;
        #server_name  localhost;
        server_name  test.starworking.com;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;
	
        location / {
            root   /home/dev/qms/;
            try_files $uri $uri/ /dist/index.html;
            index  /dist/index.html;

        }

	location ~ /(api|pdf2png|attachments|downloadPdf|downloadExcel)/.* {
	        add_header Access-Control-Allow-Origin $http_origin always;
                add_header Access-Control-Allow-Credentials true always;
                add_header Access-Control-Allow-Methods 'GET,POST,PUT,DELETE,OPTIONS' always;
                add_header Access-Control-Allow-Headers 'Authorization,X-Requested-With,Content-Type,Origin,Accept' always;
		
		access_log  logs/api.access.log main;	

		proxy_pass http://10.0.1.166:6888;
		proxy_read_timeout 600s;
		proxy_set_header Host $http_host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
	}


        error_page  404 405           /404.json;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.json;
        location = /50x.json {
            return 200 '{"code":500, "message":"接口异常"}';  
        }

	location = /404.json {
            return 200 '{"code":400, "message":"接口不存在"}';
        }


    }


}
```







## Mac安装

```
brew install nginx    // 安装nginx
nginx -v    // 显示版本号

cd /usr/local/etc/nginx
sudo nginx 或者 nginx
关闭nginx
　　sudo nginx -s stop 或者 nginx -s stop
重启nginx
　　sudo nginx -s reload 或者 nginx -s reload
```



#### 配置https

https://www.jianshu.com/p/092049445f15



## Http转Https IE安装SSL 证书

### 1. 使用openSSL手动生成的证书

https://blog.csdn.net/smartdt/article/details/80027579

```
openssl req -x509 -nodes -days 36500 -newkey rsa:2048 -keyout /usr/local/ssl/nginx.key -out /usr/local/ssl/nginx.crt
```



### 2. 导出证书

![image-20201119231447746](/Users/star/Desktop/XJJ/notes/Nginx.assets/image-20201119231447746.png)



### 3. 安装证书

![image-20201119231636745](/Users/star/Desktop/XJJ/notes/Nginx.assets/image-20201119231636745.png)

### 4. https信任访问

![image-20201119231800518](/Users/star/Desktop/XJJ/notes/Nginx.assets/image-20201119231800518.png)