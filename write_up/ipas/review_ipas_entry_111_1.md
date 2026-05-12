# iPAS 資安工程師初級考古題 111-1 錯題檢討

## 資訊安全技術概論
**下列何者為輕型目錄存取協定（Lightweight Directory Access Protocol, LDAP）較常使用之通訊埠（Port）？**  
(A) 311 (B) 123 **(C) 389** (D) 390  

關鍵判斷：  
- `LDAP` 是輕型目錄存取協定，常用於查詢與管理目錄服務，例如帳號、群組、組織單位等資訊。
- `LDAP` 預設常用通訊埠為 `389`；若是加密版本 `LDAPS`，常用通訊埠為 `636`。
- `123` 為 `NTP` 網路時間協定使用之通訊埠。

---
**下列何者「不」是作業系統更新所使用的指令？**  
(A) wuauclt (B) apt-get ***(C) update*** (D) yum  

關鍵判斷：  
- Windows 可使用 `wuauclt` 觸發 Windows Update 相關操作。  
- Debian / Ubuntu 系列常用 `apt-get` 進行套件更新。`apt-get update` 中的 `update` 則是 `apt-get` 的子命令，不是獨立的作業系統更新工具。  
- Red Hat / CentOS 系列常用 `yum` 進行套件更新。  
- `update` 本身不是常見作業系統更新指令。  

---
**請問下列何者「並非」行動裝置上唯一識別號碼？**  
(A) 通用唯一識別碼（Universally Unique Identifier, UUID）  
(B) 國際移動用戶識別碼（International Mobile Subscriber Identity, IMSI）  
(C) 國際移動設備識別碼（International Mobile Equipment Identity, IMEI）  
***(D) 國際基頻版本識別碼（International Baseband Version Identity, IBVI）***  

關鍵判斷：  
- `UUID`：通用唯一識別碼，可用於識別裝置、應用或資料物件。
- `IMSI`：國際移動用戶識別碼，用於識別行動用戶，通常與 SIM / 行動網路用戶身分有關。  
- `IMEI`：國際移動設備識別碼，用於識別行動設備本身；IMEI 是行動設備常見唯一識別碼。  
- `IBVI`：看起來像硬湊的名詞，選它。

---
**在駭客工具中，常見到中國菜刀（China Chopper）或相似工具，其主要手法為下列何者？**  
***(A) 通過向網站提交一句簡短的程式碼，來達到向伺服器插入木馬，並最後獲取 webshell***  
(B) 針對網站，建立一個連接，以很低的速度發包，並保持住這個連接不斷開，最後將可用的連線佔滿  
(C) 客戶使用主機 M 訪問並登錄合法網站 webA 後，再去訪問惡意網站 webB，然後惡意網站webB 冒充該客戶透過使用者主機 M 去向網站 webA 發起請求  
(D) 使用不安全的反序列化漏洞，利用遠端執行任意程式碼進行注入攻擊  

關鍵判斷：  
- `China Chopper` 是常見的 webshell 管理工具，通常搭配「一句話木馬」使用。攻擊者先將簡短的後門程式碼植入伺服器端，再透過工具連線控制該 webshell，進行檔案管理、指令執行等操作。

選項解析：  
- (A) 一句話木馬 / webshell，正確。
- (B) 低速連線佔滿資源，這是 `Slowloris` 類型 DoS 攻擊。
- (C) 使用者登入合法網站後，被惡意網站誘導發請求，這是 `CSRF`。
- (D) 不安全反序列化導致遠端程式碼執行，這是反序列化導致 `RCE`。

---
**請問撰寫安全程式碼，可參考下列何項資料？**  
(A) NIST SP 800 系列 (B) FIPS 系列 (C) ISO 27000 系列國際標準 ***(D) OWASP 指南***  

關鍵判斷：  
`OWASP` 主要關注 Web 應用程式安全，提供安全開發、弱點防護、測試與實作建議，例如 OWASP Top 10、OWASP Secure Coding Practices、OWASP Cheat Sheet Series 等。  

判斷規則：  
- `安全程式碼`、`Web 弱點`、`XSS / SQLi / CSRF` → `OWASP`
- `管理制度`、`ISMS` → `ISO 27000`
- `美國資安控制／風險管理／技術建議` → `NIST SP 800`
- `聯邦標準／密碼模組` → `FIPS`

---
**「封包來源端 IP 與目的端 IP 相同的攻擊。」屬於下列何種攻擊方法？**  
(A) Smurf Attack ***(B) Land Attack*** (C) UDP Flood Attack (D) ICMP Flood Attack  

關鍵判斷：  
`Land Attack` 的特徵是攻擊封包的**來源 IP 與目的 IP 設成相同**，甚至來源 port 與目的 port 也可能相同，讓目標主機在處理連線時產生異常或資源耗損。  

判斷規則：  
- 來源 IP = 目的 IP → `Land Attack`
- ICMP + 廣播 + 偽造受害者來源 → `Smurf Attack`
- 大量 UDP → `UDP Flood`
- 大量 ICMP → `ICMP Flood`

---
## 資訊安全管理概論
**組織已開始著手進行資訊資產之盤點、建立清冊，並實施風險評鑑作業，請問此作業屬於 PDCA 循環之何者階段？**  
(A) P（Plan） **(B) D（Do）** (C) C（Check） (D) A（Act）  

關鍵判斷：  
本題描述組織已開始進行資訊資產盤點、建立清冊，並實施風險評鑑作業。  
題庫將這些「實際執行資產盤點與風險評鑑」視為 PDCA 循環中的 `Do` 階段。  

易錯原因：  
- 從一般管理直覺來看，資產盤點與風險評鑑也可能被理解為規劃資安管理制度的前置工作，因此容易選 `Plan`。  
- 但 iPAS 題庫已不只一次將「資訊資產盤點／風險評鑑作業」歸入 `Do`，考試時應依題庫分類處理。  

判斷規則：  
- 政策、目標、制度規劃 → `Plan`
- 題庫邏輯：資產盤點、建立清冊、實施風險評鑑 → `Do`
- 監控、稽核、檢查成效 → `Check`
- 矯正、改善、持續改進 → `Act`

---
**關於自然人憑證，下列敘述何者「不」正確？**  
(A) 使用非對稱式演算法產生金鑰對  
***(B) 簽驗章和加解密是使用同一組金鑰對***  
(C) 目前自然人憑證設有有效期，但可以展延  
(D) 透過自然人憑證進行簽章時，被簽章之資料無長度限制  

觀念釐清：
自然人憑證使用非對稱式加密技術，並採用雙金鑰對設計：  
- 簽章／驗章：一組金鑰對
- 加密／解密：另一組金鑰對

另外，實務上簽章通常是對資料雜湊後的摘要進行簽章；然而內政部 FAQ 說，透過自然人憑證進行簽章時，送入雜湊前的資料長度沒有限制。

---
**一般而言，公開公鑰會透過憑證管理中心發行公開憑證來傳遞，對於仍在有效期內，卻因為某些因素造成憑證廢止的情形，可以透過下列何項協定來查詢？**
***(A) Online Certificate Status Protocol（OCSP）***  
(B) Online Certificate Register Protocol（OCRP）  
(C) Online Certificate Revoke Protocol（OCRP）  
(D) Certificate Transmit Protocol（CTP）  

關鍵判斷：  
- 憑證雖然仍在有效期限內，但可能被憑證管理中心廢止。  
- 若要即時查詢憑證是否仍有效、是否已遭撤銷，可使用 `OCSP`。  

判斷規則：  
- 查憑證是否撤銷／仍有效 → `OCSP`
- 憑證撤銷清冊 → `CRL`
- 本題其他選項均為魚目混珠

---
**下列何種人員負責風險評鑑後風險處理與殘餘風險結果的核可？**  
(A) 資產擁有者（Asset Owner）  
***(B) 風險擁有者（Risk Owner）***  
(C) 設備擁有者（Device Owner）  
(D) 資料擁有者（Data Owner）  

關鍵判斷：  
- 風險評鑑後，對於風險處理方式與殘餘風險是否可接受，通常應由 `風險擁有者` 核可。
- 因為殘餘風險的意思是：

    > 即使採取控制措施後，仍然留下來、需要組織承擔的風險。

  誰要承擔這個風險，誰就要負責核可。這不是設備誰買的、資料誰管的問題，而是風險最後由誰接受。

判斷規則：  
- `資產管理責任` → Asset Owner
- `資料分類與資料使用責任` → Data Owner
- `設備管理責任` → Device Owner
- `風險處理、殘餘風險接受／核可` → Risk Owner

---
**關於 IPSec 金鑰管理機制，下列敘述何者正確？**  
(A) IPSec 使用 SKIP 作為金鑰管理協議  
(B) IPSec 將 IKE 作為候選協議且從未實作  
(C) SKIP 協議分為兩版本：SKIPv1 和 SKIPv2  
***(D) SKIP 為 IKE 金鑰管理協議的前身***  

關鍵判斷：  
- `IPSec` 需要金鑰管理機制來協商安全關聯與加密金鑰。實務與標準中常見的是 `IKE`。
- `SKIP` 是早期的 IP 安全金鑰管理協議方案，可視為 IKE 之前的相關技術或前身，但後來 IPSec 主要採用 IKE。
- `IKE` 有 `IKEv1` / `IKEv2`
