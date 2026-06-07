# ⚡ Tank World — 联机坦克大战

实时网络双人坦克对战游戏，基于 WebSocket 同步，支持局域网 / Radmin LAN / ZeroTier 跨网联机。

## 快速开始

```bash
# 安装依赖
npm install

# 启动服务器
node server.js
```

两台设备的浏览器打开 `http://<服务器IP>:3000`，进入大厅后自动匹配对战。

## 操作

| 操作 | 按键 |
|------|------|
| 移动 | `W` `A` `S` `D` |
| 射击 | `空格` |
| 重新开始 | `R` |

## 架构

```
server.js   ← WebSocket 游戏服务器（权威逻辑，60fps tick）
index.html  ← 客户端（渲染 + 输入采集）
```

- 所有碰撞、伤害、胜负判定在服务端完成
- 客户端每帧发送输入，接收状态同步
- 子弹可反弹墙壁，有障碍物掩体

## 跨网络联机

使用 Radmin LAN / ZeroTier / Tailscale 等虚拟局域网工具：

1. 主机加入虚拟网络，获取虚拟 IP
2. `node server.js` 启动服务
3. 客户端输入虚拟 IP 连接

## License

MIT
