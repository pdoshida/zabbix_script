# 手順実施における成果物
- zabbix server 4.0 LTS
- zabbix action

## requeired
- amzn2
- t3.small 以上相当のインスタンスタイプ

## Zabbixサーバーインストール
1. AmazonLinux2作成
2. rootでシェル実行  
./install_zabbix4_amzn2.sh
3. ブラウザからzabbix初期設定を行う  
http://${INSTANCE_GLOBAL_IP}/zabbix

## Zabbix設定リソース
**Action**
```
名前：
適当なの

デフォルトの件名： （復旧の件名も同様）
{TRIGGER.STATUS}: {TRIGGER.NAME} : {HOST.NAME1}({TRIGGER.HOSTGROUP.NAME})

デフォルトのメッセージ：　（リカバリメッセージも同様）
{TRIGGER.STATUS}: {TRIGGER.NAME} : {HOST.NAME1}({TRIGGER.HOSTGROUP.NAME})
```
**アクションの実行条件**
```
And/Or A and B
A メンテナンスの状態
B トリガーの値=障害
```
**アクションの実行内容**
```
ユーザーグループにメッセージを送信
```

