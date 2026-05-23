# iPAS 資安工程師初級考古題 114-2 錯題檢討

## 資訊安全技術概論
**在 Windows 作業系統中，下列何項功能之主要目的用來限制某些應用程式的執行，以提升系統安全性？**  
(A) Microsoft IoT Defender  
(B) BitLocker  
***(C) AppLocker***  
(D) Task Scheduler  

關鍵判斷：  
`AppLocker` 是 Windows 的應用程式控制功能，可根據規則限制或允許程式執行，例如：

- 可執行檔 `.exe`
- Windows Installer
- Script
- DLL
- Packaged apps

可依據發行者、路徑、檔案雜湊等條件建立允許或拒絕規則。  

判斷規則：  
- AppLocker → 限制／允許應用程式執行
- BitLocker → 磁碟加密
- Task Scheduler → 排程

---
**下列哪一個漏洞未在 OWASP Cloud-Native Application Security Top 10之中？**  
(A) Injection flaws  
(B) Improper authentication & authorization  
(C) Insecure secrets storage  
***(D) Server-Side Request Forgery***  

關鍵判斷：  
`OWASP Cloud-Native Application Security Top 10` 與一般 `OWASP Top 10 Web Application Security Risks` 不是同一份清單。

Cloud-Native Application Security Top 10 中包含：

- `Injection Flaws`
- `Improper Authentication & Authorization`
- `Insecure Secrets Storage`

但 `Server-Side Request Forgery（SSRF）` 是 OWASP Top 10 2021 Web Application Security Risks 的項目，不是本題所問的 Cloud-Native Application Security Top 10 項目。  

---
**下列何項驗證「不」是專門針對雲端機房的驗證制度？**  
(A) CSA STAR ***(B) SOC 2*** (C) ISO/IEC 27017 (D) ISO/IEC 27018  

關鍵判斷：  
- `CSA STAR`：Cloud Security Alliance 的雲端安全評鑑／登錄制度，明確針對雲端服務。
- `SOC 2`：服務組織控制報告，不限於雲端機房或雲端服務。
- `ISO/IEC 27017`：雲端服務資訊安全控制措施指引。
- `ISO/IEC 27018`：公有雲中個人可識別資訊 PII 保護控制措施。

---
## 資訊安全管理概論
**ISO/IEC 27001: 2022 相較 ISO/IEC 27001: 2013，主要新增控制措施「不」包括下列何項？**  
(A) 新增使用雲端服務之資訊安全  
(B) 新增網頁過濾要求  
***(C) 新增技術漏洞管理要求***  
(D) 新增資料洩漏預防要求  

關鍵判斷：  
ISO/IEC 27001:2022 Annex A 相較 2013 版，確實新增了一些控制措施，例如：

- 使用雲端服務之資訊安全
- 網頁過濾
- 資料洩漏預防
- 威脅情資
- ICT 營運持續整備
- 設定管理
- 資訊刪除
- 資料遮罩
- 監控活動等

但 `技術漏洞管理` 在 ISO/IEC 27001:2013 就已存在，不是 2022 版新增控制措施。

---
**貴公司是大型銀行的供應商之一，主要負責銀行客戶個資處理及利用；而最近因應數位轉型計劃，打算將相關基礎建設遷移至雲服務，試問為滿足客戶需求及服務品質保證，公司導入下列何種標準最「不」適當？**  
***(A) ISO 27006*** (B) ISO 27001 (C) ISO 27701 ***(D) ISO 27018***  

關鍵判斷：  
本題公司是銀行供應商，負責客戶個資處理與利用，並將基礎建設遷移至雲服務。

適合導入的標準包含：
- `ISO 27001`：資訊安全管理系統，建立整體 ISMS。
- `ISO 27701`：隱私資訊管理系統，強化個資／隱私管理。

爭議選項：
- `ISO 27006` 則是針對提供 ISMS 稽核與驗證之機構的要求，不是一般企業導入資安管理或個資保護的標準。
- `ISO 27018`：公有雲中個人可識別資訊 PII 保護控制措施。

---
**企業為確保資通系統及資產得以識別，進行資通資產分類時，其中定義資產種類包含主要性（primary）資產及支援性（supporting）資產等兩種類型。請問，下列何項資產及類型配對結果為正確？**  
**1. 資訊（information）：主要性**  
**2. 硬體（hardware）：主要性**  
**3. 網路（network）：支援性**  
**4. 人員（personnel）：主要性**  
**5. 業務流程（business processes）：支援性**  
**6. 企業活動（business activities）：主要性**  
(A) 1、4、6 ***(B) 1、3、6*** (C) 2、3、5 (D) 2、4、5  

關鍵判斷：  
- 主要性資產 primary asset → 組織真正要保護的「內容／活動／流程」
- 支援性資產 supporting asset → 用來承載、處理、傳輸、維持主要性資產的「工具／環境／人員」

---
**FIDO（Fast Identity Online）是無密碼登入解決方案，主要是透過公開金鑰加密的架構結合終端裝置的多重因素驗證（MFA）與生物辨識驗證進行登入動作，可以更嚴密地保護個資。請問下列關於 FIDO 的描述何者較「不」正確？**  
(A) FIDO 的三大認證協議分別為 FIDO UAF、FIDO U2F、FIDO2  
(B) FIDO 的最大特色是所有協定都建立於公開金鑰加密上，讓伺服器端只保存公鑰，不再需要負責保管使用者個資  
***(C) 使用者於各家金融機構先進行身分驗證開通「金融 FIDO」的使用，就可以利用個人終端裝置而不需要攜帶金融卡進行各項金融服務的驗證***  
(D) 使用者可以在終端裝置上透過指紋辨識、聲音辨識、輸入個人識別碼 PIN 等方式進行線上登入  

關鍵判斷：  
`FIDO` 的核心是使用公開金鑰密碼學進行身分驗證：

- 伺服器端保存公鑰。
- 使用者裝置端保存私鑰。
- 使用者透過 PIN、生物辨識等方式在本機解鎖私鑰。
- 裝置用私鑰簽署 challenge。
- 伺服器用公鑰驗證簽章。

但「金融 FIDO」不代表使用者可以在所有金融服務中完全不使用金融卡。  
其適用範圍仍受金融機構支援項目、服務類型、風險等級與法規要求限制。

---
**美國「網路安全暨基礎設施安全局」（CISA）規範了用以識別及分類資通安全威脅情資（Cyber Threat Intelligence, CTI），並指定可以閱讀或共享 CTI 接收者的管理指導準則《Traffic Light Protocol 2.0 User Guide》，其中規範 CTI 敏感程度的 TLP（Traffic Light Protocol）標籤共有 4 種。請問是下列何項？**  
**1. RED 2. GREEN 3. BLACK 4. BLUE 5. WHITE 6. CLEAR 7. AMBER**  
(A) 1、2、3、4 (B) 2、3、5、6 ***(C) 1、2、6、7*** (D) 1、4、5、7  

關鍵判斷：  
TLP 2.0 的四種標籤為：
- 紅燈：RED
- 黃燈：AMBER
- 綠燈：GREEN
- 清空／公開：CLEAR

版本燈號修改：  
- TLP 1.0：WHITE
- TLP 2.0：CLEAR
