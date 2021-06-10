## laravel_worker项目使用方法

1. 复制 `.env.example` 为 `.env`，配置数据库信息，并自行在 `mysql` 中建一个对应的数据库。
2. `composer install` 安装相关包。
3. `php artisan key:generate` 生成应用Key。
4. `php artisan migrate` 运行迁移生成数据表。
5. 使用 `php artisan serve` 启动服务。
6. 打开一个新命令行窗口，`cd socket/GatewayWorker`
7. `php start.php start`启动 `socket` 服务。
8. 访问 `http://localhost:8000`，并自行注册账号。

## win下可能出现无法连接

此问题只发生在 `windows` 操作系统中，`linux` 与 `mac` 中没有此问题。
所有的 `0.0.0.0`，需要修改成 `127.0.0.1`


1.请在 `socket/GatewayWorker/Applications/YourApp/start_gateway.php` 中，修改为

```php
$gateway = new Gateway("websocket://127.0.0.1:8282");
```

2.`resources/assets/js/components/ChatRoom.vue` 中，修改为

```javascript
let ws = new WebSocket("ws://127.0.0.1:8282");
```
