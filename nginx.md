### Nginx常用配置


> 禁用缓存

no-cache和private属性值仍然会请求服务器，询问文件是否有改变。no-store是直接告诉浏览器不保存文件，每次都请求服务器获取文件
```
server {
        listen       80;
        server_name  hostname.com;

        add_header Cache-Control no-cache;
        add_header Cache-Control private;
        add_header Cache-Control no-store;

        location / {
            root /services/apps/demo;
            index index.html;
        }
}
```

> Nginx处理隐藏目录

```
 server {
        listen       80;
        server_name  your_server_name;

        # 需要放在最前面
        location ^~ /. {
            return 404;
        }
        location / {
            root /services/apps/project_name;
        }
```
