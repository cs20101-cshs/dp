# iPAS 資安工程師初級考古題 109-1 錯題檢討

## 資訊安全技術概論
**行動通訊網路到哪一代之後，語音與數據通訊皆採用IP架構運作？**  
(A) 2G 通訊 (B) 3G 通訊 ***(C) 4G 通訊*** (D) 5G 通訊  

關鍵判斷：  
- `3G`：數據通訊能力提升，但**語音仍多採電路交換**。
- `4G / LTE`：All-IP 架構，語音可透過 VoLTE 以 IP 方式運作。
- `5G`：延續 IP 化架構，但不是開始的世代。

判斷規則：  
- 看到「語音與數據皆 IP 化」或 `All-IP`，先想到 `4G / LTE`。

---
**Intel X86 作業系統之核心模式（Kernel Mode），被設計於中央處理器（CPU）的何種特權等級中執行？**  
(A) Ring 3 (B) Ring 2 (C) Ring 1 ***(D) Ring 0***  

關鍵判斷：  
Intel x86 架構使用特權環（Privilege Rings）區分執行權限。`Ring 0` 權限最高，作業系統核心（Kernel）通常在 `Ring 0` 執行；一般應用程式則在 `Ring 3` 執行。

判斷規則：  
- 看到 `Kernel Mode`、核心模式、OS kernel → `Ring 0`。  
- 看到 `User Mode`、一般應用程式 → `Ring 3`。

---
**WannaCry 勒索病毒植入電腦後會將該電腦之檔案進行加密，請問該勒索病毒是利用微軟的何種漏洞來執行？**  
(A) Microsoft XML Core Services  
(B) Shellshock 漏洞  
***(C) 伺服器訊息區塊（SMB）漏洞***  
(D) Local Security Authority Subsystem Service（LSASS）  

關鍵判斷：  
`WannaCry` 勒索病毒主要利用 Windows `SMBv1` 漏洞進行散播，常見關鍵字為 `EternalBlue`、`MS17-010`。

判斷規則：  
- 看到 `WannaCry` → 想到 `EternalBlue / MS17-010 / SMBv1`。

---
**下列何者「不」是和雲端安全有關的國際標準？**  
***(A) ISO/IEC 27011*** (B) ISO/IEC 27017 (C) ISO/IEC 27018 (D) CSA STAR  

關鍵判斷：  
- `ISO/IEC 27011`：偏電信組織資訊安全管理，不是雲端安全標準。
- `ISO/IEC 27017`：雲端服務資訊安全控制措施指引。
- `ISO/IEC 27018`：公有雲中個人資料保護相關實務準則。
- `CSA STAR`：Cloud Security Alliance 的雲端安全評鑑／認證制度。

判斷規則：  
- 看到雲端安全標準，優先想到 `ISO/IEC 27017`、`ISO/IEC 27018`、`CSA STAR`。  
- 看到 `ISO/IEC 27011`，想到**電信業**。

---
## 資訊安全管理概論
**關於控制的類型，下列何者「不」正確？**  
(A) 嚇阻性：為了讓有犯意的人，因恐懼而產生放棄，如：違反條款  
(B) 偵測性：為了事件發生時，能夠產生警訊而察覺，如：入侵偵測  
(C) 預防性：為了避免不希望的事情發生，如：設立門禁卡  
***(D) 指導性：為了回復至正常運作的措施，如：回復正確設定***  

觀念釐清：
- 嚇阻性 Deterrent Control：讓人因為害怕後果而不敢做  
例：違反條款、警告標語、法律責任、監視器告示  
- 偵測性 Detective Control：事件發生時或發生後能察覺  
例：入侵偵測 IDS、日誌監控、稽核紀錄  
- 預防性 Preventive Control：事前阻止事件發生  
例：門禁卡、防火牆、權限控管、多因素驗證  
- 矯正性 Corrective Control：事件發生後修復、恢復正常  
例：回復正確設定、還原備份、修補漏洞  
- 指導性 Directive Control：告訴人應該怎麼做，引導行為  
例：政策、程序、標準、教育訓練、作業規範  

關鍵判斷：  
題目說「回復至正常運作」，這是 `Corrective Control`，也就是矯正性控制，不是 `Directive Control` 指導性控制。

判斷規則：  
- 看到「回復、修復、還原、補救」→ 矯正性控制。  
- 看到「政策、程序、標準、教育訓練、要求怎麼做」→ 指導性控制。

---
**若公司高階管理層希望對公司採取 ISO/IEC 27001 資訊處理措施，實施多重備援（Redundancies），應屬於下列何種控制措施？**  
(A) 紀錄之保護 (B) 系統安全測試 (C) 保護應用服務交易 ***(D) 資訊處理設施之可用性***  

觀念釐清：
- 備援 / Redundancy / Failover / HA → 可用性 Availability
- 備份 Backup → 資料保護、復原能力，不要和備援混成一坨

關鍵判斷：  
`Redundancies` 指多重備援，目的在於當部分資訊處理設施故障時，仍可由其他設備或系統接手，維持服務運作，因此屬於可用性相關控制措施。  

判斷規則：  
- 看到 `備援`、`冗餘`、`redundancy`、`failover`、`HA` → 先想到 `Availability 可用性`。  
