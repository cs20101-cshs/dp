# iPAS 資安工程師初級考古題 110-2 錯題檢討

## 資訊安全技術概論
**關於網路型入侵偵測系統（Network Intrusion Detection System, NIDS），下列敘述何者正確？**  
(A) 安裝後對於網路流量的影響很大  
(B) 安裝後可以保護所有電腦不被入侵  
(C) 其資料來源是作業系統、應用程式或網路登入/登出紀錄（Log）  
***(D) 若流量（Traffic）太高，可能會影響攻擊偵測準確度***  

關鍵判斷：  
- `NIDS` 是網路型入侵偵測系統，主要透過監聽網路流量來偵測可疑封包或攻擊行為。若網路流量過高，設備可能來不及分析所有封包，造成漏判、封包遺失或偵測準確度下降。
- `NIDS` 多半採**旁路監聽**或**鏡像流量**方式部署，通常不會大幅影響正常網路流量。

判斷規則：  
- `NIDS` → 看網路封包／流量
- `HIDS` → 看主機紀錄、系統 log、檔案異動、登入登出
- `IDS` → 偵測、告警，不保證阻擋
- 流量過高 → NIDS 可能漏判或準確度下降

---
**下列何種攻擊「不」會造成系統處理效率下降？**  
(A) 死亡偵測攻擊（Ping-of-Death Attack）   
(B) 分割重組攻擊（Teardrop Attack）  
***(C) 中間人攻擊（Man-In-The-Middle Attack）***  
(D) 分散式攻擊（Distributed Attack）  

關鍵判斷：  
- `Ping-of-Death`：利用異常大小或破碎封包造成系統處理異常，可能讓系統當機或效能下降。
- `Teardrop Attack`：利用 IP 分片重組漏洞，讓系統在重組封包時出錯，可能造成當機或效能下降。
- `MITM`：中間人攻擊，主要是偷聽、竄改、冒充，不以降低系統效率為主要目的。
- `Distributed Attack`：分散式攻擊，通常指多來源攻擊，若是 DDoS 類型會造成資源耗盡與效能下降。

判斷規則：  
- `Ping-of-Death`、`Teardrop` → 都是老派封包異常攻擊，會拖垮或打掛系統。  
- `Distributed Attack` → 多來源壓流量或資源，會影響效能。
- `MITM` → 站在中間偷看／改資料，不是讓系統變慢。

---
**小明利用 ssh 命令從主機 A 首次成功的連接至主機 B，請問下列何種 ssh 檔案將會被更新？**  
(A) 主機 B 上的 `~/.ssh/authorized_keys` 檔案  
(B) 主機 A 上的 `~/.ssh/authorized_keys` 檔案  
***(C) 主機 A 上的 `~/.ssh/known_hosts` 檔案***  
(D) 主機 B 上的 `~/.ssh/known_hosts` 檔案  

關鍵判斷：  
- 小明從主機 A 首次 SSH 連線到主機 B。
- 第一次連線時，主機 A 會收到主機 B 的 host key 指紋，詢問是否信任。若使用者確認，主機 B 的 host key 會被記錄在主機 A 的：`~/.ssh/known_hosts`
- 之後主機 A 再連線到主機 B，就會比對這個紀錄，確認是不是同一台主機，避免中間人攻擊。

判斷規則：  
- `known_hosts`：我這台主機曾經連過哪些遠端主機。
- `authorized_keys`：誰的 public key 可以登入我這台主機。

---
**請問永恆之藍（EternalBlue）弱點是基於下列何種機制所產生的？**  
***(A) Windows SMB*** (B) Windows Kerberos (C) Windows RDP (D) Windows UAC  

關鍵判斷：  
- `EternalBlue` 是針對 Windows `SMBv1` 的遠端程式碼執行弱點。攻擊者可透過 SMB 服務傳送特製封包，造成目標系統被遠端利用。
- `WannaCry`、`NotPetya` 拿 `EternalBlue` 作傳播工具。
- `Kerberos`：身分驗證協定。
- `RDP`：遠端桌面協定，常見暴力破解或 `BlueKeep` 等弱點。
- `UAC`：使用者帳戶控制，偏本機權限提升或執行權限提示。

---
**若程式在源碼檢測時，發現存在可能遭受到有心人士的中間人攻擊（Man-In-The-Middle Attack, MITM）的漏洞，下列何者較可能為存在的主要問題？**  
(A) 無稽核（Lack of Auditing）  
***(B) 無憑證檢查（Lack of Certificate Verification）***  
(C) 無邊界檢查（Lack of Boundary Check）  
(D) 無輸入驗證（Lack of Input Validation）  

關鍵判斷：  
- 中間人攻擊（MITM）的常見風險之一，是通訊雙方無法確認對方身分。
- 若程式使用 HTTPS / TLS 等加密通訊，但沒有正確驗證憑證，攻擊者可能偽造憑證或攔截連線，讓使用者誤以為自己正在連到合法伺服器。  

判斷規則：  
- `MITM` → 憑證驗證、伺服器身分驗證、TLS 驗證。
- `Boundary Check` → buffer overflow / 記憶體越界。
- `Input Validation` → SQL injection / XSS / command injection。
- `Auditing` → log / 稽核 / 事後追蹤。

---
**在網站弱點檢測報告中，發現系統存在跨網站指令碼（Cross-Site Scripting, XSS）及開放式重定向（Open Redirect）攻擊問題，可以採取下列何者方案進行修補？**
(A) XSS 可以透過過濾此符號 “<”，即可根治  
(B) Open Redirect 可以採用圖像式驗證即可根治  
***(C) HTML.Encode 是可以解決 XSS 的一種方法***  
(D) XSS 可以採用 Prepared Statement 解決  

關鍵判斷：  
- `XSS` 的核心問題是使用者輸入或不可信資料被直接輸出到網頁中，讓瀏覽器當成 HTML / JavaScript 執行。
- `HTML Encode`，或稱輸出編碼，可以把特殊字元轉成 HTML entity，使瀏覽器把它當成文字顯示，而不是當成標籤或 script 執行。  
- 例如：  
    `<script>alert(1)</script>` 經 HTML Encode 後可能變成：

    `&lt;script&gt;alert(1)&lt;/script&gt;`

    瀏覽器就會顯示文字，而不是執行 script。

判斷規則：  
- `XSS` → 輸出編碼、HTML Encode、Context-aware Encoding、CSP、輸入驗證輔助。
- `SQL Injection` → Prepared Statement / Parameterized Query。
- `Open Redirect` → redirect URL 白名單、限制只能跳本站或可信網域。
- 看到「根治」兩字要小心，通常過度保證。

---
**下列何者較「不」是在軟體逆向工程動態分析時會使用到的手法？**
(A) 設定中斷點 (B) 顯示堆疊（stack）內容 (C) 單步執行 ***(D) 程式碼重構***  

關鍵判斷：  
- 軟體逆向工程的**動態分析**，是在程式執行時觀察其行為，常搭配除錯器進行中斷點設定、單步執行、檢視堆疊與記憶體內容等操作。
- `程式碼重構` 是軟體開發中的程式碼整理與改善手法，通常指在不改變外部行為的前提下改善程式結構，不是逆向工程動態分析時的典型手法。

判斷規則：
- `動態分析` → 程式跑起來，用 debugger 看行為。
- `靜態分析` → 不執行程式，看反組譯、反編譯、字串、檔案結構。
- `程式碼重構` → 開發維護，不是逆向分析。

---
## 資訊安全管理概論
**若您希望能估計營運可承受之最長中斷時間（Maximum Tolerable Period of Disruption），最有可能從下列何者取得？**  
(A) 平衡計分卡（Balanced Score Card）  
(B) 風險評鑑（Risk Assessment）  
(C) 恢復點目標（Recovery Point Objective）  
***(D) 營運衝擊分析（Business Impact Analysis）***  

關鍵判斷：  
- `MTPD`，Maximum Tolerable Period of Disruption，指的是某項業務或服務可以承受的最長中斷時間。
- 這種「業務中斷多久會造成不可接受影響」的問題，通常要透過 `BIA` 營運衝擊分析取得。
- `BIA` 會分析：
    - 哪些業務流程是關鍵業務
    - 中斷會造成什麼影響
    - 中斷多久會不可接受
    - 需要多快恢復
    - 資源與優先順序怎麼排  

判斷規則：  
- `MTPD`：最長可容忍中斷時間 → `BIA`
- `RTO`：多久內要恢復服務 → 通常由 `BIA` 推導
- `RPO`：資料最多可遺失到哪個時間點，重點是「資料損失容忍度」，不是最長中斷時間
- `Risk Assessment`：風險可能性與影響評估
- `平衡計分卡`：績效管理工具  
