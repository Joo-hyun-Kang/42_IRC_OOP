# 42 プロジェクト  
**<ft_irc> (参加者: jokang、taehykim、mikim3, )**  
<img width=80% height=80% alt="irc_photo" src="https://github.com/user-attachments/assets/71768bd8-b3e6-459e-b992-5f1986eb1050">

<br>

## IRCプロトコルの使用  
- **IRC参考資料**: [RFC2812](https://datatracker.ietf.org/doc/rfc2812/)  
- **プロジェクト概要**:  
  非同期式ノンブロッキングマルチプレクサを利用したTCP通信チャットプログラムのサーバー部分を開発。  
  クライアント(Client)、サーバー(Server)、チャンネル(Channel)をそれぞれオブジェクトとして管理。  

- **使用言語**: C++  
- **使用関数**: `poll`  

<br>

## 使用方法  

### サーバー側
```bash
make  
./ircserv <ポート番号> <パスワード>
//ircserv 9191 1234

```

<br>

### クライアント側  
#### ncを利用して接続
```bash
nc <アドレス> <ポート番号>
PASS <Server Password>
NICK <NickName>
USER <user> <mode> <unused> <realname>

/* Example
#ログイン
nc 127.0.0.1 9191
PASS 1234
NICK jokang
USER jokang * * joohyunKang

#チャットルーム&メッセージ発送
JOIN #tokyo
PRIVMSG #tokyo :Hello World! 

*/

JOIN #<チャンネル> - チャンネル作成および参加
PART #<チャンネル> - チャンネルから退出
PRIVMSG <ユーザー> :<メッセージ> - チャンネル内でメッセージを送信
QUIT - 接続終了
MODE #<チャンネル> +o <ニックネーム> - オペレーター権限の移譲
MODE #<チャンネル> +k <パスワード> - チャンネルパスワードの設定
MODE #<チャンネル> +l <人数> - チャンネルの人数制限設定
KICK #<チャンネル> <ニックネーム> - チャンネルからユーザーを強制退去
NOTICE #<チャンネル> :<メッセージ> - 公告メッセージ送信
NICK <ニックネーム> - ニックネームの変更
```

<br>

#### irssiを利用して接続
```bash
brew install irssi  - irssi(IRCクライアント)設置
irssi  - irssi実行
/connect <アドレス> <ポート番号> <パスワード> <ユーザー名>
//connect 127.0.0.1 9191 1234 mikim


チャンネル作成および参加：/join #<チャンネル>
チャンネルから退出：/part #<チャンネル>
接続終了：/quit - 
irssiを終了：/exit
オペレーター権限の移譲：/mode #<チャンネル> +o <ニックネーム> 
チャンネルパスワードの設定：/mode #<チャンネル> +k <パスワード>
チャンネルの人数制限設定：/mode #<チャンネル> +l <人数>
チャンネルからユーザーを強制退去：/kick #<チャンネル> <ニックネーム>
公告メッセージ送信：/notice #<チャンネル> :<メッセージ>
ニックネームの変更：/nick <ニックネーム>
```
