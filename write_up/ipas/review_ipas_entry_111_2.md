# iPAS 資安工程師初級考古題 111-2 錯題檢討

## 資訊安全技術概論
**請問下列何者為常見的 SNMP（Simple Network Management Protocol）安全問題？**  
***(A) 使用 public community string***  
(B) 使用 SNMP v3  
(C) 使用 UDP  
(D) 使用 161 作為服務 Port  

關鍵判斷：  
- SNMP v1 / v2c 常使用 community string 作為存取控制。  
- 若使用預設或容易猜測的 community string，例如 `public`，攻擊者可能讀取設備資訊，甚至在具寫入權限時修改設定。

判斷規則：  
- `SNMP` + `public/private community string` → 安全問題。
- `SNMP v1/v2c` → community string，安全性較弱。
- `SNMP v3` → 認證、加密，較安全。
- `UDP 161` → SNMP 正常服務 port。  

---
**下列何者攻擊是透過 UDP（User Datagram Protocol）協定送出假造來源的廣播封包至目標網路，以便產生擴大資料流量效果的阻絕服務攻擊？**  
(A) Smurf ***(B) Fraggle*** (C) Land (D) Teardrop  

關鍵判斷：  
- `Fraggle Attack` 是利用 UDP 廣播封包進行放大攻擊。攻擊者偽造來源 IP 為受害者，將 UDP 封包送到目標網路的廣播位址，讓多台主機回應受害者，造成流量放大與阻斷服務。

判斷規則：  
- `ICMP` + 廣播 + 偽造來源 → `Smurf`
- `UDP` + 廣播 + 偽造來源 → `Fraggle`
- 來源 IP = 目的 IP → `Land`
- 分片重組異常 → `Teardrop`

---
**下列何者為遠端使用者撥入驗證服務（Remote Authentication Dial In User Service，RADIUS）常使用之通訊埠（Port）？**  
***(A) 1812*** (B) 123 (C) 389 (D) 390  

關鍵判斷：  
- `RADIUS` 是遠端使用者撥入驗證服務，常用於網路設備、VPN、無線網路等身分驗證情境。 
- RADIUS 驗證服務常用 `UDP 1812`，計費／記錄服務常用 `UDP 1813`。

判斷規則：  
- `RADIUS` → `1812`
- `RADIUS Accounting` → `1813`
- `NTP` → `123`
- `LDAP` → `389`

---
**通訊埠（Port）是應用層每種服務皆有的唯一埠號碼，其範圍介於 0~65536。其中 1024 之前為公認通訊埠（Well-Known Port），關於通訊埠用途的敘述，下列何項錯誤？**  
(A) Port:53/TCP 用途：DNS 域名解析服務  
***(B) Port:123/UDP 用途：LDAP 輕型目錄存取協定***  
***(C) Port:445/UDP 用途：Microsoft-DS SMB 檔案分享***  
(D) Port:995/TCP 用途：基於 SSL 的 POP3 收發電子郵件加密傳輸  
**備註：port 範圍應該是 `0~65535`

關鍵判斷：  
- `123/UDP` 是 `NTP`，用於網路時間同步。
- `LDAP` 常用通訊埠是 `389`，`LDAPS` 為 `636`。
- SMB / Microsoft-DS 檔案分享實務上主要使用 `TCP 445`，題目寫成 `445/UDP`，因此也可視為錯誤。

判斷規則：  
- `DNS` → 53 TCP/UDP
- `NTP` → 123 UDP
- `LDAP` → 389
- `LDAPS` → 636
- `SMB / Microsoft-DS` → 445 TCP 為主
- `POP3S` → 995 TCP

---
**請問要重送 TCP 封包需要使用下列何項工具？**  
(A) Wireshark ***(B) Tcpreplay*** (C) ngrep (D) hping  

關鍵判斷：  
- `Tcpreplay` 用來重播封包擷取檔，例如 pcap，常用於測試 IDS/IPS、防火牆、網路設備或流量分析環境。  

判斷規則：  
- `Wireshark`：封包擷取與分析工具，主要用來看封包。
- `Tcpreplay`：可重播封包流量。
- `ngrep`：類似 network grep，可用來搜尋／監看網路封包內容。
- `hping`：可自訂與產生封包，用於測試或掃描，但不是本題「重送封包」的最佳答案。

---
**請問下列哪個 SSL Cipher Suite「不」安全應停用？**  
***(A) RC4*** (B) AES256 (C) AES512 (D) AES128  

關鍵判斷：  
- `RC4` 是舊式串流加密演算法，已知存在多種安全弱點，不建議再用於 SSL/TLS 加密連線，因此相關 cipher suite 應停用。  

判斷規則：  
- `RC4` → 舊、不安全、SSL/TLS 應停用。
- `AES128 / AES256` → 常見安全對稱加密。
- `DES / 3DES / RC4 / NULL / EXPORT` → 看到就要警覺。

---
**在現行 Fedora/CentOS/RHEL Linux 中記錄登入系統如 SSH（Secure Shell） 等遠端連線登入紀錄為下列何者？**  
***(A) /var/log/secure***  
(B) /var/log/messages  
(C) /var/log/wtmp  
(D) /var/log/null  

關鍵判斷：  
- 在 Fedora / CentOS / RHEL 系 Linux 中，SSH 登入、sudo、su、認證成功或失敗等安全與身分驗證相關紀錄，常見於：`/var/log/secure`
- Debian / Ubuntu 則是 `/var/log/auth.log`

判斷規則：  
- `/var/log/secure`：Red Hat 系常見安全／認證紀錄位置，包含 SSH 登入紀錄。
- `/var/log/messages`：一般系統訊息紀錄，範圍較廣。
- `/var/log/wtmp`：記錄登入登出歷史，可用 `last` 指令讀取。
- `/var/log/null`：不存在的干擾項。要也是 `/dev/null`。

---
**公司高階主管近日購買一部 Macbook Pro，內含新版的 MacOS，由於業務上的關係，此主管經常攜帶筆電外出商談開會，因此公司的資安顧問建議他啟用某一項功能以防範筆電遺失被偷時，仍能夠避免資料外洩，請問該高階主管需要啟用下列何項系統功能？**  
(A) Bitlocker (B) TrueCrypt (C) EncFs ***(D) FileVault***  

關鍵判斷：  
- 主管常攜帶 MacBook Pro 外出，風險是筆電遺失或遭竊後，硬碟資料被他人讀取。
- macOS 內建的磁碟加密功能為 `FileVault`，可加密啟動磁碟，降低裝置遺失時資料外洩風險。

判斷規則：  
- `Windows` 磁碟加密 → `BitLocker`
- `macOS` 磁碟加密 → `FileVault`
- `TrueCrypt`：舊式跨平台加密工具，已停止維護
- `EncFS`：檔案系統層級加密工具
- 遺失筆電防資料外洩 → 啟用全磁碟加密

---
**下列何項駭客工具可以傾倒（dump）記憶體裡登入過的帳號密碼？**  
***(A) mimikatz*** (B) SQLmap (C) Burp Suite (D) AppScan  

關鍵判斷：  
- `mimikatz` 是常見的 Windows 憑證擷取工具，可從記憶體或系統中擷取登入憑證、雜湊值、Kerberos ticket 等資訊。常見於滲透測試、紅隊演練，也常被惡意程式濫用。

判斷規則：  
- 記憶體帳密 / Windows credential dumping → `mimikatz`
- SQL Injection → `SQLmap`
- Web Proxy / Repeater / Intruder → `Burp Suite`
- Web 弱掃 → `AppScan`

---
**請問 CWE（Common Weakness Enumeration）是指下列何項？**  
(A) 常見漏洞和風險編號 ***(B) 弱點種類*** (C) Exploit Code (D) 漏洞修補建議  

關鍵判斷：  
`CWE` 是 `Common Weakness Enumeration`，中文可理解為「常見弱點列舉」。  
它是在分類與描述軟體或系統中的**弱點類型**，例如：  
- SQL Injection
- Cross-Site Scripting
- Buffer Overflow
- Improper Input Validation
- Hard-coded Credentials

所以 CWE 不是單一漏洞編號，也不是 Exploit Code，而是**弱點種類分類**。

判斷規則：  
- `CVE` → 具體漏洞編號  
- `CWE` → 弱點種類分類  
- `CVSS` → 漏洞嚴重度評分  
- `Exploit` → 利用程式碼／攻擊利用方式

---
**關於 MS-SQL Server 內建備份方式的敘述，下列何者錯誤？**  
***(A) 完整備份會截斷交易記錄***  
(B) 要做任何差異備份或交易記錄備份之前，一定要做一次完整備份  
(C) 差異備份不會備份任何交易記錄檔  
(D) 交易記錄檔備份透過 SSMS 操作，在預設的情況下會自動截斷交易記錄  

關鍵判斷：  
- SQL Server 的完整備份（Full Backup）會備份整個資料庫，但**不會截斷交易記錄**。
- 交易記錄是否截斷，通常和交易記錄備份、復原模式有關。在**完整復原模式**（Full Recovery Model）下，必須進行**交易記錄備份**，才會讓已備份的交易記錄可被截斷。

判斷規則：  
- `Full Backup`：不截斷交易記錄
- `Differential Backup`：備份自上次完整備份後變更的資料
- `Transaction Log Backup`：備份交易記錄，可讓 log 截斷

---
**關於 WPA（Wi-Fi Protected Access），下列敘述何者「不」正確？**  
(A) 初始向量（Initialization Vector，IV）長度：48 位元  
(B) WPA 支援 TKIP（Temporal Key Integrity Protocol）加密方式 　
(C) 封包驗證方式：CRC（Cyclic Redundancy Check）　 
***(D) 加密方法：3DES***  

關鍵判斷：  
WPA（Wi-Fi Protected Access）常見特徵：  
- IV 長度：48 位元
- 支援 TKIP（Temporal Key Integrity Protocol）
- 加密機制：TKIP，底層仍使用 RC4 類型機制
- 完整性保護：TKIP 加入 MIC / Michael 等機制強化封包完整性

判斷規則：  
- `WEP` → RC4、24-bit IV、CRC-32
- `WPA` → TKIP、48-bit IV、MIC / Michael
- `WPA2` → AES-CCMP
- `3DES` → 不是 WPA 加密方法

---
## 資訊安全管理概論
**關於公務機關未遵守資通安全管理法規定的敘述，下列何者正確？**  
(A) 應按其情節輕重，依相關規定按次處新臺幣十萬元以上一百萬元以下罰鍰  
(B) 應按其情節輕重，依相關規定按次處新臺幣三十萬元以上五百萬元以下罰鍰  
***(C) 應按其情節輕重，依相關規定予以懲戒或懲處***  
(D) 應按其情節輕重，依相關規定按次處新臺幣三萬元以上五十萬元以下罰鍰  

關鍵判斷：  
- 《資通安全管理法》對公務機關所屬人員未依規定辦理者，採取的是懲戒或懲處，而不是直接處以罰鍰。  

---
**關於 AD（Active Directory）與 LDAP（Lightweight Data Access Protocol）兩者比較的敘述，下列何者正確？**  
(A) AD 是用來交談的協議，也就是目錄資料的協議規範  
(B) LDAP 是一目錄服務，通過 IP 協議提供訪問控制和維護分布式資訊  
***(C) AD 網域的基本物件包含了 Domain Controllers、Computers、Builtin、Users***  
(D) LDAP 提供唯讀型網域控制站的網域控制站角色  

關鍵判斷：  
- `AD`（Active Directory）是 Microsoft 的目錄服務，用來管理網域中的使用者、電腦、群組、網域控制站等物件。  
- `LDAP` 是存取目錄資料的協定，用來查詢、存取與維護目錄資訊。

判斷規則：  
- `AD` → Microsoft 目錄服務／網域管理系統。
- `LDAP` → 存取目錄資料的協定。
- 問網域控制站、Users、Computers、Builtin → AD。
- 問目錄查詢協定、port 389 → LDAP。

---
**某位安全性分析師負責整合企業的單一登入（Single Sign-On，SSO）解決方案，解決方案需要採用開放性的標準，並且在許多不同網頁應用程式間交換認證及授權訊息，下列何者為分析師最應提出的建議方案？**  
(A) RADIUS ***(B) SAML*** (C) TACACS+ (D) XTACACS  

關鍵判斷：  
- `SAML`（Security Assertion Markup Language）是開放標準，常用於 Web 單一登入（SSO）情境，用來在身分提供者（IdP）與服務提供者（SP）之間交換認證與授權資訊。  

判斷規則：  
- `RADIUS`：常用於網路設備、VPN、無線網路等 AAA 驗證
- `SAML`：Web SSO 常見開放標準
- `TACACS+`：Cisco 常見 AAA 協定，多用於網路設備管理認證
- `XTACACS`：TACACS 的舊版本

---
**量子電腦運算（Quantum Computing）技術日益成熟，其對於現代密碼學影響的敘述，下列何項錯誤？**  
(A) 非對稱密碼學（Asymmetric Cryptography）可被有效破解  
***(B) 對稱式密碼學（Symmetric Cryptography）面臨巨大風險而需全數汰換***  
(C) 後量子密碼學（Post-Quantum Cryptography）可抵抗量子電腦運算優勢  
(D) CRYSTALS-Kyber、FALCON、Classic McEliece 皆為後量子密碼學演算法  

關鍵判斷：  
- 量子電腦對非對稱密碼學影響最大。RSA、Diffie-Hellman、ECC 等公鑰密碼系統，在大型量子電腦與 Shor’s algorithm 下會面臨嚴重威脅。
- 對稱式密碼學也會受 Grover’s algorithm 影響，使暴力搜尋效率提升，但通常可透過增加金鑰長度來因應，例如使用 AES-256。  

判斷規則：  
- `量子電腦` + `非對稱密碼` → RSA / DH / ECC 危險。
- `量子電腦` + `對稱式密碼` → 增加金鑰長度，不是全數汰換。
- `PQC` → 抵抗量子攻擊。
- `CRYSTALS-Kyber / FALCON / Classic McEliece` → 後量子密碼相關演算法。

---
**附圖為 Kerberos 的簡略認證過程，圖中使用者取得的二個票證（Tickets），依序分別為下列何種票證？**  
***(A) Ticket-granting Ticket(TGT)、Service Ticket(ST)***  
(B) Service Ticket(ST)、Ticket-granting Ticket(TGT)  
(C) Master Ticket(MT)、Service Ticket(ST)  
(D) Client Ticket(CT)、Server Ticket(ST)  

關鍵判斷：  
Kerberos 認證流程中，使用者不會一開始就直接拿到服務票證。  
- 第一階段：使用者向 Authentication Server（AS）認證，成功後取得 `Ticket-granting Ticket（TGT）`。  
- 第二階段：使用者拿 `TGT` 向 Ticket Granting Server（TGS）請求特定服務的票證，取得 `Service Ticket（ST）`。  
- 第三階段：使用者拿 `Service Ticket` 去存取目標服務。  

判斷規則：  
- 第一次認證成功 → 取得 `TGT`
- 用 `TGT` 去換服務票 → 取得 `ST`
- 拿 `ST` 存取實際服務

---
**關於安全事件管理的敘述，下列何者錯誤？**  
(A) 藉由完整的資安管理制度密切掌握重要服務的日誌現況  
(B) 良好的安全資訊與事件管理機制應達到法規遵循以及威脅管理兩個主要目標  
(C) 風險矩陣：定義事件類別風險係數及設備服務重要性賦予資產價值  
***(D) OSSIM 是一個常見商業化之安全資訊管理系統***  

關鍵判斷：  
- `OSSIM` 是 `Open Source Security Information Management`，屬於**開源**安全資訊與事件管理系統。
- 補充：OSSIM 是歷史上常見的開源 SIEM / SIM 工具；現行使用時仍需確認維護狀態。  

判斷規則：  
- `SIEM` → Security Information and Event Management
- `OSSIM` → Open Source Security Information Management
- 看到 `OSSIM` + `商業化` → 小心

---
**營運持續的過程中，在(甲)備援中心將重要服務回復至最低可接受水準，與最後於(乙)原地重建之階段。其重啟服務順序應為下列何項？**  
(A) (甲)(乙)都先回復最重要系統  
***(B) (甲)最重要系統先回復(乙)最重要系統最後才回復***  
(C) (甲)最重要系統最後才回復(乙)最重要系統先回復  
(D) (甲)(乙)最重要系統都最後才回復  

關鍵判斷：  
- （甲）備援中心將重要服務回復至最低可接受水準：這是災難發生後的應急恢復階段，目標是讓關鍵業務先活下來，所以應優先恢復最重要系統。
- （乙）原地重建之階段：這是從備援狀態逐步回復到原正式環境。此時重要系統可能已經在備援中心運作，為避免再次中斷，通常會先恢復較不關鍵系統，確認原地環境穩定後，最後再把最重要系統切回來。

判斷規則：  
- 災難發生，切到備援中心：`最重要系統先恢復`
- 原地重建，從備援切回正式環境：`最重要系統最後切回`
