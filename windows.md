# Windows Tunnel
### 操作前準備及注意事項
- 需先有至少一台可以連接內網機器的電腦

### 操作中步驟
- 先於跳板機輸入netsh interface portproxy add v4tov4 listenport=3390 listenaddress=0.0.0.0 connectport=3389 connectaddress={內網IP}
- 再於host端輸入192.168.182.138:3390，即可RDP內網機器，直接拿到shell

### 操作後步驟及注意事項
- 取得內網機器的權限，可於自己的windows直接連接內網的機器
- 須注意因為跳板機上的另一張網卡會占用3389，所以需先用第一步轉開port，或把另一張網卡的RDP服務關掉才能用3389轉發

### 指令範例
- 192.168.182.138:3390 
- ![](https://i.imgur.com/icqn1K9.png)
- ![](https://i.imgur.com/IkmZq1h.png)

