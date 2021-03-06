﻿[![https://gyazo.com/8adf55449db0d5a1f063105abb0dabe0](https://i.gyazo.com/8adf55449db0d5a1f063105abb0dabe0.jpg)](https://gyazo.com/8adf55449db0d5a1f063105abb0dabe0)

# 基本的な操作シナリオ Aamazon Web Service (AWS)
### ～Webサーバ構築編～
## はじめに
AWS における基本的な操作シナリオ(Webサーバ構築編)(以下、本シナリオ)では、AWS環境上で初めてサーバを構築する際の基本的な操作手順を示しています。

ここでは、できるだけシンプルでかつ、構築したサービスが動作しているという実感を得られるよう考慮し、Webサーバを構築してみます。

## 環境と前提条件

本シナリオは、下図のようなシンプルなクラウドデザインを想定して作成しています。

[![https://gyazo.com/d4dd51e4fa91eecc81db4800fc061a55](https://i.gyazo.com/d4dd51e4fa91eecc81db4800fc061a55.png)](https://gyazo.com/d4dd51e4fa91eecc81db4800fc061a55)

本シナリオに示す操作を行うために、クラウド利用者はWebブラウザを使用できる必要があります。
また、EC2インスタンス上での作業用に、TeratermやPutty（または、Linuxの各種Terminal）からSSHクライアントを実行できる必要があります。

尚、本シナリオを作成するに当たり、下記のソフトウェアを用いて動作確認を行いました。

| 項目 | ソフトウェア | 補足 |
|:-----------|:------------|:------------|
| OS       | Wndows 8 | 32bit     |
| Webブラウザ   | chrome | 特別なプラグインは不要  |
| SSHクライアント   | teraterm | EC2インスタンスへログインしない場合は、不要。  |

2015年12月28日現在、AWSでは下記のブラウザをサポートしています。

| ブラウザ | バージョン | サービス |
|:------------|:-------------|:---------------|
| Google Chrome | 直近の 3 バージョン | すべてのサービス |
| Mozilla Firefox | 直近の 3 バージョン | すべてのサービス |
| Microsoft Internet Explorer | 11、10、9 | すべてのサービス |
| Microsoft Edge | 12 | すべてのサービス |
| Apple Safari | 9、8、7、6 | すべてのサービス |

## 注意
AWSは従量課金型パブリッククラウドサービスです。
本シナリオを実施する際には、EC2インスタンス使用料、EBS使用料、ネットワーク通信料等が発生します。
また、本シナリオを終了した後にインスタンスの削除、EBSの削除、EIPの削除等を行わないと継続して課金されますのでご注意ください。

本シナリオでは、ルートユーザではなくIAMユーザにて操作する手順となっておりますので、
ログイン画面などルートユーザで操作する場合と若干差異があります。

本シナリオについては、事前にAmazon Web Services社の承認は得ていません。個々に記載している内容は、Amazon Web Services社の公式なステートメントではないのと同時に、企業からの依頼・要請によりコンテンツが予期せず廃止となる場合があり
ますので、あらかじめご了承ください。

本シナリオでは2015年12月28日現在のマネジメントコンソール画面のスクリーンショットを使用して説明しています。
以降にAmazon Web Services社がUIを変更した際には、本シナリオの画像と実際の画面が異なることがございます。

## 無料利用枠
AWSでは新規アカウント登録者に対し、無料利用枠を提供しております。  
AWS 無料利用枠には、AWS にサインアップした日から 12 か月間お使いいただける無料利用枠の付いたサービスと、12 か月間の無料利用期間終了後にも自動的に期限切れにならない追加サービスが提供されています。  
[AWSクラウド無料利用枠の詳細](https://aws.amazon.com/jp/free/)

本シナリオは無料利用枠内で利用できる内容となっているため、実質無料で気軽に体験していただけます。

## 本シナリオのゴール
本シナリオは、AWS上に実際にプライベートネットワークを構築し、その上でEC2インスタンスを起動します。     EC2インスタンスへ外部からアクセスが可能なように設定を行いながら、実際にEC2インスタンスをWebサーバとして稼働させます。

[シナリオを始める](https://github.com/yoshirako/aws-handson-scenario/blob/master/WebServer/Scenario/01-Login-to-ManagementConsole.md)
