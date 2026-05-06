# iPAS 資安工程師初級考古題 108-2 錯題檢討

## 資訊安全技術概論
**下列何者「不」是微軟網路芳鄰常見使用 Port?**
(A) 137 (B) 139 (C) 123 (D) 445

網路上的芳鄰使用 port:
UDP 137, 138 -> NetBIOS Name & Datagram
TCP 139 -> NetBIOS over TCP/IP
TCP 445 -> 直接託管 SMB，Windows 2000 以後使用

---
**下列程式碼片段存在安全瑕疵,請問下列何者可達成 SQL Injection 攻擊?**
```
String query = "SELECT * FROM accounts WHERE custID='" +
request.getParameter("id") + "'";
```
(A) `id = 0 OR 1`
(B) `custID = 1 or 1`
(C) `'1'='1'`
(D) `' or '1'='1`

SQL最後會長成：
```SQL
SELECT * FROM accounts WHERE custID='使用者輸入的 id'
```
輸入(D)之後，代入變成：
```SQL
SELECT * FROM accounts WHERE custID='' or '1'='1'
```
看到 `'1'='1'`，資料就全部倒出來了

---
**關於密碼潑灑(Password Spraying),下列敘述何者正確?**
(A) 用單一弱密碼,嘗試登入所有帳號
(B) 蒐集常見的密碼,放入字典,嘗試登入系統
(C) 利用外洩的帳號與密碼組合,嘗試登入系統
(D) 使用所有可能密碼組合,嘗試登入系統

密碼潑灑攻擊是一種暴力破解攻擊，惡意行為者會嘗試**對多個帳戶**使用同一個密碼，接著再嘗試另一個密碼。密碼潑灑攻擊的效果通常很好，因為許多使用者使用的都是簡單、易於猜測的密碼。

正如「潑灑」一詞所指，**密碼潑灑攻擊的一個特點是，其一次鎖定的目標可能是數千個、甚至是數百萬個不同的使用者，而不只是一個帳戶**。過程通常是自動化的，而且可能會長時間進行，以避開偵測。

---
**一般在進行資安日誌分析時,若想分析 Linux 系統中使用者的登入歷史紀錄,應蒐集下列何種檔案?**
(A) `/var/log/messages`
(B) `/etc/login.defs`
(C) `/var/log/secure`
(D) `/var/log/dmesg`

`/var/log/wtmp` 成功登入歷史，搭配 last
`/var/log/btmp` 失敗登入紀錄，搭配 lastb
`/var/run/utmp` 目前登入中的使用者，搭配 who / w
`/var/log/lastlog` 每個使用者最後一次登入紀錄，搭配 lastlog
`/var/log/auth.log` Debian/Ubuntu 系統的認證與登入相關紀錄
`/var/log/secure` RHEL/CentOS 系統的認證與登入相關紀錄

其他選項解析：
`/var/log/messages` 系統一般訊息日誌，很多 daemon、kernel、服務訊息會進去，但不是專門登入紀錄。
`/etc/login.defs` 登入相關設定檔，例如密碼期限、UID/GID 範圍等。
`/var/log/dmesg` 核心開機訊息，硬體、驅動、kernel ring buffer 那類。

---
## 資訊安全管理概論
**關於風險評估(Risk Evaluation),下列敘述何者正確?**
(A) 是識別風險來源、事件、發生的原因,與可能產生的後果 
(B) 是組織進行風險評鑑、識別、分析的整體流程 
(C) 是理解風險本質並且決定風險等級的流程 
(D) 是比較風險分析結果與風險準則來決定風險或嚴重程度是否為可接受的流程

(A) 風險識別 Risk Identification
(B) 風險評鑑 Risk Assessment 的整體流程。
(C) 風險分析 Risk Analysis

- **風險識別 Risk Identification**：找出風險是什麼
- **風險分析 Risk Analysis**：分析風險多嚴重、多可能
- **風險評估 Risk Evaluation**：拿分析結果去跟準則比較，看能不能接受
- **風險評鑑 Risk Assessment**：上面三個合起來的整體流程

---
**在進行營運持續規劃時,若評估發現公司資料遺失之最大可接受程度為 10 分鐘內,應考慮下列何者?**
(A) 恢復點目標 (Recovery Point Objective, RPO)
(B) 恢復時間目標 (Recovery Time Objective, RTO)
(C) 工作恢復時間 (Work Recovery Time, WRT)
(D) 最大可容忍中斷時間 (Maximum Tolerable Period of Disruption, MTPD)

- RPO = 可以接受資料倒退多久
- RTO = 系統要多久恢復上線
- WRT = 系統恢復後，業務作業要多久恢復正常
- MTPD = 最長可以忍受中斷多久，超過就出大事
