# grpc-demo
- php client 
  -  Lumen (7.2.0) (Laravel Components ^7.0)
  - composer install
- golang server
  - go run main.go

## 安装时注意事项

1. Class 'Grpc\ChannelCredentials' not found？

   >1. 去https://pecl.php.net/package/gRPC，选择一个较新的稳定版，点击Downloads列下的DLL，下载对应32或64位系统，线程安全或不安全的版本
   >
   >2. 将下载包解压，将php_grpc.dll放入php扩展目录，默认是ext目录下
   >
   >3. 在php.ini中添加 extension=php_grpc.dll
   >
   >4. 重启php

2. Class 'Google\Protobuf\Internal\Message' not found

   ```php
   composer require google/protobuf
   ```

## PHP作为客户端原因

采用PHP作为client, Golang作为Server端，PHP目前只支持作为客户端的角色实现。我们知道由于PHP语言特性本身不支持内置提供强大的HTTP服务，借助于fastcgi与nginx或者apache等工作，所以这个也是不支持作为gRPC server服务端的主要原因。

