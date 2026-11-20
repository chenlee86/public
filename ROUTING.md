# 分流规则

## v2rayN

`v2rayn-advanced.json` 是路由规则数组，使用与 v2rayN 路由规则编辑器相同的格式。导入方式视版本而定；如果不能直接导入数组，请复制或按规则逐项添加。检查节点名称是否与本地完全一致。规则从上到下匹配，YouTube 位于 Google 之前。规则依赖安装的 geosite.dat / geoip.dat 含相应分类；不存在的分类需要删去或更新数据。

## Karing

`karing/broker.json` 和 `karing/ai.json` 是 sing-box source 格式规则集，不是 Karing 整体配置，也不包含出站策略。在自定义分流组的 Rule Set 中分别添加以下地址，并选择出口：

- 券商：https://raw.githubusercontent.com/chenlee86/public/main/karing/broker.json
- AI：https://raw.githubusercontent.com/chenlee86/public/main/karing/ai.json

AI 集只包含明确域名和 IP；另外在 Karing 的规则集选择界面启用 AI、Google、YouTube 等分类，YouTube 放在 Google 之前。其他类别按需使用 Karing 内置分类；各类别分别选择出口。

## Shadowrocket

`shadowrocket/routing.conf` 是可粘贴到现有配置的 `[Rule]` 段，不含节点或代理组。将其内容替换现有配置的规则段，并在应用中配置 PROXY。可按需为 YouTube、AI、券商另建策略并把对应行的 PROXY 改为策略名称。远程 RULE-SET 的获取依赖第三方规则源。

## 注意

这些文件是匹配规则，不含节点、账户或 DNS 配置。券商规则包括共享 CDN 域名和未经独立核实的 IP 段，可能误匹配；规则集和节点应定期检查。全局 UDP 443 阻断影响所有应用；Karing 中需自行添加该规则。IP 匹配行为受 DNS、内核与路由设置影响，建议在真实应用中检查日志。
