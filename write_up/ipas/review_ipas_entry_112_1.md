# iPAS 資安工程師初級考古題 112-1 錯題檢討

## 資訊安全技術概論
**以下何者為通用型的弱點掃描工具（Vulnerability Scanner）？**  
(A) Nmap ***(B) OpenVAS*** (C) OWASP (D) SCAP  

關鍵判斷：  
- `OpenVAS` 是常見的開源弱點掃描工具，可用來掃描系統、服務與網路設備是否存在已知弱點，因此屬於通用型 vulnerability scanner。  
- `SCAP`：Security Content Automation Protocol，是安全組態與弱點管理相關標準／協定集合，不是通用型掃描工具本身。

判斷規則：  
- `Nmap` → Port / Service 掃描
- `OpenVAS` → 弱點掃描工具
- `OWASP` → Web 安全組織／指南／Top 10
- `SCAP` → 安全內容自動化標準  

---
**基於安全性考量，管理員需要重檢視一部 Linux 系統的檔案權限，請問下列哪一個命令可以找出 Linux 系統中所有已被設定 SUID 的程式檔案？**  
***(A) `find / -perm -4000 -type f`***  
(B) `find / -perm -2000 -type f`  
(C) `find / -type +6000 -print`  
(D) `find / -type suid`  

關鍵判斷：  
Linux 檔案特殊權限中：  
- `SUID`：`4000`
- `SGID`：`2000`
- `Sticky bit`：`1000`  

find 語法：
- `-type f`：搜尋類型為「檔案」
- `-perm`：搜尋權限

因此答案為 `find / -perm -4000 -type f`

---
**請問在 Linux 環境中十分著名的漏洞（Dirty Cow, CVE-2016-5195），以下針對這個漏洞的描述何者錯誤？**  
***(A) 此漏洞是在 Linux PAM（Pluggable Authentication Modules for Linux）機制上的異常，可以取得使用者的密碼***  
(B) 此漏洞主要是 Linux 核心記憶體處理子程序的異常所產生  
(C) 利用此漏洞可以進行本地端服務提權  
(D) 這個漏洞也會影響特定版本之 Android 手機  

關鍵判斷：  
- `Dirty COW`，CVE-2016-5195，是 Linux kernel 的 Copy-on-Write 機制競爭條件漏洞。 
- 攻擊者可利用此漏洞在本地端進行權限提升，將原本不應修改的唯讀記憶體映射內容寫入，進一步取得更高權限。

判斷規則：  
- Dirty COW → Linux kernel / Copy-on-Write / 本地提權
- 不是 PAM，不是偷密碼題

---
**關於憑證填充攻擊（Credential Stuffing）的敘述，下列何者錯誤？**  
(A) 通常使用殭屍網路（Botnet）進行攻擊  
(B) 會以自動化方式試圖登入網路服務  
(C) 可使用雙因子認證（two-factor authentication）  
***(D) 會直接造成網路服務中斷，影響可用性***  

關鍵判斷：  
- `Credential Stuffing` 是攻擊者使用已外洩的帳號密碼組合，透過自動化工具大量嘗試登入不同網路服務。
- 其目標通常是取得帳號存取權，而不是直接癱瘓服務。

判斷規則：  
- `Credential Stuffing` → 外洩帳密 + 自動化登入嘗試。
- 防禦方式 → 2FA、異常登入偵測、rate limiting、CAPTCHA、密碼重設、IP / 裝置風險評分。
- 直接造成服務中斷 → DoS / DDoS。

---
**下列何者「不」是資料隱碼攻擊（SQL Injection）類型？**  
***(A) Frame-Based SQL injection***  
(B) Error-Based SQL injection  
(C) Time-Based SQL injection  
(D) Union-Based SQL injection  

關鍵判斷：  
常見 SQL Injection 類型包含：  
- `Error-Based SQL Injection`：利用資料庫錯誤訊息取得資訊。
- `Time-Based SQL Injection`：利用延遲回應時間判斷條件是否成立。
- `Union-Based SQL Injection`：利用 `UNION SELECT` 合併查詢結果。
- `Boolean-Based SQL Injection`：利用真假條件造成不同頁面反應。  

判斷規則：  
- `Error-Based` → 看錯誤訊息
- `Time-Based` → 看延遲時間
- `Union-Based` → 用 `UNION SELECT`
- `Boolean-Based` → 典型例子：`OR '1'='1`

---
**從 Microsoft 安全性開發週期（Secure Development Life, SDL）的觀點，縮小攻擊面向（Attack Surface Reduction），主要是下列何項階段的考量？**  
(A) 需求階段（Requirements）  
***(B) 設計階段（Design）***  
(C) 實作階段（Implementation）  
(D) 發佈階段（Release）  

關鍵判斷：  
- 縮小攻擊面向（Attack Surface Reduction）是在設計系統時，盡量減少可被攻擊者利用的入口、服務、功能、介面與權限暴露。通常屬於安全**設計階段**的考量，而不是等到實作或發佈才補救。  

判斷規則：  
- `安全需求`、`隱私需求`、`合規要求` → Requirements
- `威脅建模`、`攻擊面縮小`、`安全架構` → Design
- `安全程式碼`、`靜態分析`、`程式碼檢查` → Implementation
- `最終安全檢查`、`事件應變計畫`、`發佈核准` → Release

---
**資料庫類型很多，常見 MS-SQL 資料庫，就有其日誌記錄，下列針對 MS-SQL 資料庫日誌敘述何者錯誤？**  
(A) 錯誤記錄檔是位於 Program Files\Microsoft SQL Server\MSSQL. n \MSSQL\LOG\ERRORLOG和ERRORLOG  
(B) MS-SQL 資料庫仍需要定期 TRANSACT 清除日誌  
(C) MS-SQL 交易記錄檔過大，透過 SQL Query 來清除其語法 DBCC SHRINKFILE （'資料庫名稱_log ', 0, TRUNCATEONLY）  
***(D) MS-SQL 記錄檔無法變更位置，因此我們必須預留相關磁碟空間，以及定期清理***  

關鍵判斷：  
MS-SQL 的資料庫檔案與交易記錄檔位置是可以變更或移動的。  
例如資料庫的 `.mdf`、`.ndf`、`.ldf` 檔案都可以透過設定、detach / attach、ALTER DATABASE 等方式調整位置。  

判斷規則：  
- ERRORLOG → 常在 MSSQL\LOG\ERRORLOG
- Transaction log → .ldf，Full backup 不截斷交易記錄，Transaction log backup 才會讓 log 可截斷
- DBCC SHRINKFILE 可縮小檔案，但不該亂用
- Log 檔位置可以變更

---
## 資訊安全管理概論
**中華民國「營業祕密法」所稱之營業祕密，係指方法、技術、製程、配方、程式、設計或其他可用於生產、銷售或經營之資訊，其所必須符合之要件，下列敘述何項錯誤？**  
(A) 非一般涉及該類資訊之人所知者  
(B) 因其秘密性而具有實際或潛在之經濟價值者  
(C) 所有人已採取合理之保密措施者  
***(D) 資訊洩漏將造成公司損失者***  

關鍵判斷：  
《營業秘密法》所稱營業秘密，須符合三個要件：  
- 非一般涉及該類資訊之人所知者。
- 因其秘密性而具有實際或潛在之經濟價值者。
- 所有人已採取合理之保密措施者。  
