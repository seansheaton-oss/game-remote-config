# 游戏远程配置

集中管理多款游戏的 AdMob 广告模式和隐私政策入口。公开文件不包含密钥或玩家数据。

## 薄荷汽车突围

游戏键：`mint-unblock-car-puzzle`。当前模式：**官方测试广告**。

编辑 [config.json](config.json) 中该游戏的 `ads.mode`：

- `test`：Google 官方 iOS 激励测试广告。
- `live`：正式广告；先填写 `ads.ios.app_id` 和 `rewarded_units` 的 `energy`、`undo`、`hint`。

正式 App ID 还必须写入游戏工程并重新导出 iOS 包，因为它属于 Info.plist 配置。发布包已包含正式 App ID 后，可通过这里切换测试／正式广告。ID 缺失或与安装包不符时，游戏提示正式广告未配置，不自动退回测试广告。

游戏启动及回到前台时获取配置（最短间隔 5 分钟）。下载失败使用上次有效缓存；无缓存默认测试模式。GitHub CDN 可能有短暂延迟。正在播放的广告不受中途配置变更影响。玩家不能修改模式。

## 奖励规则

- 体力不足 30 时可观看；每次奖励 5 点，最高 30。
- 每次撤销一步、获取一次提示，都需获得一次激励广告奖励。
- 取消、失败或未获得奖励回调，不发放奖励。

## 加入其他游戏

在 `games` 下新增独立的游戏键，复制现有字段结构，并让对应客户端读取该键。不要覆盖已有游戏。

## 隐私政策

[薄荷汽车突围隐私政策](https://zhanghaichao.github.io/mint-unblock-car-puzzle/privacy.html)

上线广告和 Game Center 前，政策内容应与实际的数据处理方式一致。
