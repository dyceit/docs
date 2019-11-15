# pm2 使用笔记

## 简介

pm2 是一个带有负载均衡功能的Node应用的进程管理器。当你要把你的独立代码利用全部的服务器上的所有CPU，并保证进程永远都活着，0秒的重载，PM2是完美的。

## 网址

官网：https://pm2.keymetrics.io/

## 安装

```
$ npm install -g pm2
```

## 项目实战

```
$ cd F:\240\project\grunt001\server
```

进入server目录（公司配置好的静态资源服务器目录） shift+右键 -> 在此处打开命令窗口

文件夹目录可以直接用shift+右键进入命令窗口

```
$ pm2 start main.js --name="asset" --watch
```

预览地址：http://asset.mangoerp.com/index.htm

## 常用命令

启动应用程序并**命名**为 "asset"：

```shell
pm2 start main.js --name="asset"
```

**监听**应用目录变化，自动重启：

```shell
pm2 start main.js --watch
```

重启所有应用：

```shell
pm2 restart all
```

## Ecosystem File

生成配置文件：

```shell
pm2 ecosystem
```

生成 ecosystem.config.js 文件如下：

```javascript
module.exports = {
  apps : [{
    name: "app",
    script: "./app.js",
    env: {
      NODE_ENV: "development",
    },
    env_production: {
      NODE_ENV: "production",
    }
  }, {
     name: 'worker',
     script: 'worker.js'
  }]
}
```

运行配置文件

```
pm2 [start|restart|stop|delete|reload] ecosystem.config.js
```

更多参见官方文档：https://pm2.keymetrics.io/docs/usage/application-declaration/#ecosystem-file

## CheatSheet

```shell
# Fork mode
pm2 start app.js --name my-api # Name process

# Cluster mode
pm2 start app.js -i 0        # Will start maximum processes with LB depending on available CPUs
pm2 start app.js -i max      # Same as above, but deprecated.
pm2 scale app +3             # Scales `app` up by 3 workers
pm2 scale app 2              # Scales `app` up or down to 2 workers total

# Listing

pm2 list               # Display all processes status
pm2 jlist              # Print process list in raw JSON
pm2 prettylist         # Print process list in beautified JSON

pm2 describe 0         # Display all informations about a specific process

pm2 monit              # Monitor all processes

# Logs

pm2 logs [--raw]       # Display all processes logs in streaming
pm2 flush              # Empty all log files
pm2 reloadLogs         # Reload all logs

# Actions

pm2 stop all           # Stop all processes
pm2 restart all        # Restart all processes

pm2 reload all         # Will 0s downtime reload (for NETWORKED apps)

pm2 stop 0             # Stop specific process id
pm2 restart 0          # Restart specific process id

pm2 delete 0           # Will remove process from pm2 list
pm2 delete all         # Will remove all processes from pm2 list

# Misc

pm2 reset <process>    # Reset meta data (restarted time...)
pm2 updatePM2          # Update in memory pm2
pm2 ping               # Ensure pm2 daemon has been launched
pm2 sendSignal SIGUSR2 my-app # Send system signal to script
pm2 start app.js --no-daemon
pm2 start app.js --no-vizion
pm2 start app.js --no-autorestart

# Startup

pm2 startup						# Restarting on server boot/reboot
pm2 save							# Freeze a process list for automatic respawn
```

