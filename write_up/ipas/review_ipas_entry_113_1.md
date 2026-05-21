# iPAS 資安工程師初級考古題 113-1 錯題檢討

## 資訊安全技術概論
**下列何者可以用來評估作業系統（Operation system）的安全性最為適切？**  
***(A) Common Criteria***  
(B) ISO/IEC 27001  
(C) IEC 62443-2-1  
(D) Cybersecurity Framework  

關鍵判斷：  
- `Common Criteria`，正式名稱是 `Common Criteria for Information Technology Security Evaluation`，常用來評估資訊技術產品或系統的安全性，例如作業系統、資料庫、防火牆、智慧卡等。它會透過安全功能需求、安全保證需求、評估保證等級等方式，評估產品是否符合特定安全目標。

判斷規則：  
- `作業系統 / IT 產品安全性評估` → `Common Criteria`
- `ISMS / 組織管理制度` → `ISO 27001`
- `工控 / ICS` → `IEC 62443`
- `組織資安風險框架` → `Cybersecurity Framework`

---
**在攻擊者已經取得系統存取權限之後，除了翻找系統有沒有高權限帳號的密碼或是嘗試破解雜湊之外，也可能會利用已知的提升權限弱點來讓自己變成 root 或 Administrator，以便取得更完整的系統控制權。請問下列何項「不」是 Windows 或 Linux 作業系統常見用來提升權限的弱點或技巧？**  
(A) Dirty COW (B) SetUID (C) Juicy Potato ***(D) Chisel***  

關鍵判斷：  
題目問的是 Windows 或 Linux 常見用來**提升權限**的弱點或技巧。    
- `Dirty COW`：Linux kernel 的 Copy-on-Write 競爭條件漏洞，可用於本地提權。
- `SetUID`：Linux 特殊權限設定，若設定不當或程式有漏洞，可被用於提權。
- `Juicy Potato`：Windows 提權技巧，利用 COM / NTLM relay 類機制取得較高權限。
- `Chisel`：主要是網路 tunneling / port forwarding 工具，不是提權工具。

---
**在 IP camera 使用時，要做下列何項串流的安全傳輸協定以避免攻擊？**  
(A) SMTPS ***(B) RTSPS*** (C) SFTP (D) RDP  

關鍵判斷：  
IP camera 常用即時串流協定：
- `RTSP`：Real Time Streaming Protocol，即時串流協定。
- `RTSPS`：RTSP over TLS，用 TLS 加密 RTSP 傳輸，以降低串流被竊聽或竄改的風險。

判斷規則：  
- `IP camera / 即時影像串流` → `RTSP`
- `安全 RTSP` → `RTSPS`
- `郵件安全傳輸` → `SMTPS`
- `檔案安全傳輸` → `SFTP`
- `遠端桌面` → `RDP`

---
**關於應用程式安全的描述，下列何者最「不」適切？**  
(A) 應用程式弱點掃描可以瞭解是不是有既有的技術性弱點  
(B) 應用程式碼的掃描可及早偵測程式撰寫的問題及可能產生的安全性問題  
***(C) 模糊測試（Fuzzing）指自動產生程式碼到原始程式中，以偵測程式碼的問題***  
(D) 應用程式的業務邏輯問題需要由熟悉業務的測試人員仔細的核實確認  

關鍵判斷：  
- `Fuzzing` 是一種自動化測試方法，透過產生大量異常、隨機、邊界或變形後的**輸入資料**，送進程式或 API，觀察是否發生錯誤、崩潰、例外或安全弱點。
- 它產生的是：`測試輸入資料`，不是：`程式碼`

判斷規則：  
- `Fuzzing` → 自動產生大量測試輸入。
- `Source Code Scan / SAST` → 掃原始碼找弱點。
- `Vulnerability Scan` → 掃既有弱點。
- `Business Logic` → 需要人工與業務脈絡確認。

---
**下列何者「不」是用在分析了解惡意程式或作為弱點管理的服務及工具？**  
***(A) archive.org*** (B) VirusTotal (C) ANY.RUN (D) vx-underground.org  

關鍵判斷：  
- `archive.org`：網際網路檔案館，主要用途是保存與查詢網頁歷史，不是惡意程式分析或弱點管理工具。
- `VirusTotal`：可上傳檔案、URL、hash，查多引擎掃描結果與威脅情資。
- `ANY.RUN`：互動式惡意程式沙箱，可觀察樣本執行行為。
- `vx-underground.org`：常見惡意程式樣本、研究資料、惡意程式相關資源站。

---
**關於數位版權管理（Digital rights management，DRM）的敘述，下列何者最「不」適切？**  
(A) DRM 是資料保護的一種方法  
(B) DRM 是一系列存取控制技術，通常用於控制數位內容和裝置在被銷售之後的使用過程  
(C) DRM 可控制使用者存取裝置和使用內容的方式  
***(D) NFT 技術可相容於現有所有的 DRM 技術***  

關鍵判斷：  
`DRM`，Digital Rights Management，是數位版權管理，通常用於控制數位內容或裝置在銷售、授權、散布後的使用方式，例如：

- 誰可以存取
- 能不能複製
- 能不能轉存
- 能不能播放
- 能不能列印
- 可以在哪些裝置上使用
- 授權到期後能否繼續使用

NFT 可以被用來表示某種數位權利或所有權憑證，但不代表它能和現有所有 DRM 技術相容，也不代表它本身就能控制內容使用。  

判斷規則：  
- `DRM` → 控制數位內容的存取、使用、複製、播放、授權。
- `NFT` → 可作為鏈上憑證或權利表示，但不是通用 DRM 相容技術。
- 看到 `所有`、`完全`、`一定` → 先懷疑。

---
**公司的官網受到駭客入侵，必須從官網 IIS Log File 來追蹤駭客來源以及手法，關於 IIS Log File 的敘述，下列何者錯誤？**  
(A) IIS 預設 log 路徑為 `%SystemDrive%\inetpub\logs\LogFiles\`  
(B) IIS 如果有多個網站 網站的 log 會在資料夾中以 `u_exyymmdd.log` 的 log 檔呈現  
***(C) 在預設狀態下，IIS 預設的日誌時間與台灣時間是一致的***  
(D) IIS提供了 4 種日誌檔格式（1）IIS 紀錄檔格式、（2）NCSA 紀錄檔案格式、（3）W3C 紀錄檔格式、（4）自定義日誌檔案格式  

關鍵判斷：  
- IIS 預設記錄檔常用 W3C 格式，而 W3C log 的 `date`、`time` 欄位通常以 **UTC** 記錄。  
- 台灣時間為 UTC+8，因此分析 IIS log 時需要進行時區換算。

判斷規則：  
- IIS log 預設路徑 → `%SystemDrive%\inetpub\logs\LogFiles\`
- IIS W3C log 檔名 → `u_exYYMMDD.log`
- IIS W3C log 時間 → 通常是 `UTC`
- 台灣時間 → `UTC+8`

---
**某系統管理員查看一 RFC 5424 協定的記錄時，其 PRI（Priority Value）為 165，請問下列個描述較為正確？**  
(A) Facility 可能是 kernel messages  
(B) Facility 可能是 NTP subsystem  
(C) Facility 可能是 local use x  
(D) Severity 可能是 Emergency: system is unusable  

關鍵判斷：  
RFC 5424 / Syslog 的 PRI 值由 Facility 和 Severity 組成：  

`PRI = Facility × 8 + Severity`

本題：

`165 = 20 × 8 + 5`

因此：

- `Facility = 20` → `local4`
- `Severity = 5` → `Notice`  

判斷規則：  
- `PRI / 8` 的商是 Facility
- `PRI / 8` 的餘數是 Severity
- Severity `0` = Emergency
- Severity `5` = Notice
- Facility `16~23` = local0~local7  

---
## 資訊安全管理概論
**ISO 27001 ISMS 最新版本已於 2022 年修正發布了，相較於前一個 2013 年版本，該文件增加了哪些安全管理用詞？**  
(A) Cybersecurity；Information Security  
(B) Privacy Protection；Information Security  
***(C) Cybersecurity；Privacy Protection；Information Security***  
(D) Cybersecurity；Information Security；Data Protection   

關鍵判斷：  
ISO/IEC 27001:2022 相較於 2013 版，標準名稱／範圍用詞納入：

- `Information security`
- `Cybersecurity`
- `Privacy protection`

---
**歐盟執委會（European Commission，EC）修正後的 2022/2555（EU）指令（即 Security of Network and Information Systems，NIS 2 Directive），已於 112 年 1 月 16 日生效，以改善歐盟現有的資訊安全態勢，本次修正內容包括擴大該指令所適用的類別與規模，附圖中哪些產業是本次新納管的產業（Sectors）？**  
**1. Drinking Water（飲用水）**  
**2. ICT service management（ICT服務管理）**  
**3. Space（太空）**  
**4. Health（健康）**  
**5. Banking（銀行）**  
**6. Waste water（廢水處理）**  
(A) 1、2、3、5、6 (B) 1、4、5、6 ***(C) 2、3、6*** (D) 1、4、6  

關鍵判斷：  
NIS 2 Directive 擴大原本 NIS Directive 的適用範圍，新增或明確納入更多產業部門。  
題目列出的項目中，新納管或擴大納入者為：

- `ICT service management`
- `Space`
- `Waste water`

---
**下列何者「非」屬 GDPR（General Data Protection Regulation）明確列入之特種個資？**  
(A) 哲學信仰 (B) 生物特徵 ***(C) 犯罪前科*** (D) 政治意見  

關鍵判斷：  
GDPR Article 9 的特種個資包含：

- 種族或族裔來源
- 政治意見
- 宗教或哲學信仰
- 工會會員身分
- 基因資料
- 用於唯一識別自然人的生物特徵資料
- 健康資料
- 性生活或性傾向資料

犯罪定罪、犯罪紀錄與相關安全措施資料則由 GDPR Article 10 另外規範，不屬於 Article 9 明確列入的特種個資。

---
**依據 CNS 27001:2023 標準條款要求有關組織應定義及應用資訊安全風險評鑑過程之敘述，下列何者錯誤？**  
(A) 建立及維持資訊安全風險準則  
(B) 資訊安全風險準則應包含風險接受準則以及執行資訊安全風險評鑑之準則  
***(C) 識別資訊安全風險包含識別資訊安全管理系統範圍內與喪失資訊之機密性、完整性、可用性以及不可否認性相關聯之風險***  
(D) 分析資訊安全風險以識別風險實際發生時，應包含可能導致的潛在後果以及風險發生的實際可能性  

關鍵判斷：  
CNS 27001:2023 / ISO/IEC 27001:2022 第 6.1.2 條「資訊安全風險評鑑」要求組織定義並應用資訊安全風險評鑑過程。其中識別資訊安全風險時，應識別 CIA 三大要素喪失相關聯之風險。其他要素都是多的。  

---
**FIDO 是確保登入流程中伺服器透過與終端裝置協定的安全機制。請問下列何項敘述有誤？**  
***(A) 由 IETF（網際網路工程任務組織）所訂定的一套網路識別標準***  
(B) 這套識別標準透過公開金鑰加密（Public Key Cryptography）的架構進行多重因素驗證（MFA）以及生物辨識登入來強力且嚴密地保護雲端帳號的個資  
(C) FIDO 是 Fast Identity Online 的縮寫  
(D) FIDO 是採用公開金鑰基礎架構的驗證模式，在 FIDO 認證伺服器端（FIDO Authentication Server）只保存相對應的公鑰，而私鑰則僅保存在使用者的 裝置端，因此使用者在登入時只需提供個資給終端裝置解鎖私鑰，再透過這個步驟解鎖公鑰進行登入  

關鍵判斷：  
- `FIDO` 是 `Fast Identity Online` 的縮寫，核心目標是減少對密碼的依賴，使用公開金鑰密碼學進行安全登入。　　  
- FIDO 是由 FIDO Alliance 推動；WebAuthn 由 W3C 標準化，CTAP 則屬 FIDO Alliance 規範。  
- FIDO 的基本模式是：
    - 使用者裝置端產生一組公私鑰。
    - 私鑰保存在使用者裝置內，不送到伺服器。
    - 伺服器保存公鑰。
    - 登入時，伺服器送出 challenge。
    - 使用者透過 PIN、生物辨識或安全金鑰等方式解鎖裝置端私鑰。
    - 裝置用私鑰簽署 challenge。
    - 伺服器用公鑰驗證簽章。
