# iPAS 資安工程師初級考古題 109-2 錯題檢討

## 資訊安全技術概論
**下列何者協定可能避免廣播風暴（Broadcast Storm）？**  
***(A) 生成樹協定（Spanning Tree Protocol, STP）***  
(B) 位址解析協定（Address Resolution Protocol, ARP）  
(C) 超文本傳輸協定（HyperText Transfer Protocol, HTTP）  
(D) 傳輸控制協定（Transmission Control Protocol, TCP）  

關鍵判斷：  
- 廣播風暴（Broadcast Storm）常見原因之一是交換器之間形成 Layer 2 網路迴圈，導致廣播封包不斷被轉送與複製。
- `STP` 可偵測交換器拓樸中的迴圈，並阻斷部分備援路徑，形成無迴圈的樹狀拓樸，以避免廣播風暴。
- `ARP` 會使用廣播來查詢 IP 對應的 MAC 位址，因此它不是避免廣播風暴的協定；在異常情況下，ARP 反而可能成為廣播流量暴增的來源之一。

判斷規則：  
- 看到「避免」 `廣播風暴`、`交換器迴圈`、`Layer 2 loop` → `STP`
- 看到 `IP 查 MAC` → `ARP`
- 看到 `ARP` 不要以為它能解決廣播風暴，它本身就是廣播使用者

---
**某公司基於安全性考量，決定將目前的 802.11 無線網路由原先的 WPA2-Personal 認證方法變更為 WPA-Enterprise，請問管理員需要在網路環境中新增管理下列何種伺服器？**  
(A) Kerberos伺服器 ***(B) RADIUS伺服器*** (C) SNMP伺服器 (D) NTP伺服器  

關鍵判斷：  
- `WPA/WPA2-Personal` 使用預共享金鑰（PSK），所有使用者通常共用同一組 Wi-Fi 密碼。  
- `WPA/WPA2-Enterprise` 則使用 `802.1X` 認證架構，常透過 `RADIUS` 伺服器進行使用者身分驗證。

選項解析：  
- `Kerberos`：常用於網域環境中的身分驗證，但不是 WPA-Enterprise 的典型新增伺服器。
- `RADIUS`：WPA-Enterprise / 802.1X 常用的認證伺服器。
- `SNMP`：用於網路設備監控與管理，不是無線使用者認證。
- `NTP`：用於時間同步，不是無線認證。

判斷規則：  
- 看到 `WPA-Enterprise`、`802.1X`、`EAP`、企業 Wi-Fi 認證 → 想到 `RADIUS`。  
- 看到 `WPA-Personal`、`PSK` → 想到共用密碼。

---
**系統管理人員於網站日誌中看見大量訊息含有類似字串「admin%27+OR+%271%27%3D%271%27+--」，請問可能為下列何種攻擊？**  
***(A) SQL資料隱碼攻擊（SQL Injection）***  
(B) 目錄遍歷（Directory Traversal）  
(C) 跨網站指令碼（Cross-Site Scripting, XSS）  
(D) 不安全的反序列化漏洞（Insecure Deserialization）  

關鍵判斷：  
日誌中的字串：`admin%27+OR+%271%27%3D%271%27+--`  
經 URL decode 後可看成：`admin' OR '1'='1' --`  

其中 `'1'='1'` 是永真條件，`--` 是 SQL 註解符號，常用來繞過原本查詢後面的條件，因此屬於 SQL Injection。  

判斷規則：  
- 看到 `%27`、`' OR '1'='1`、`--` → 想到 `SQL Injection`。
- 看到 `../`、`..%2f` → 想到 `Directory Traversal`。
- 看到 `<script>`、`onerror=`、`javascript:` → 想到 `XSS`。
- 看到序列化物件、反序列化、物件注入 → Insecure Deserialization

---
## 資訊安全管理概論
**在個資法中，關於個資隱私損害賠償的規範，當被害人無法證明實際損害金額的時候，可以請求法院依傷害情節，以多少金額計算？**  
(A) 每人一事件新台幣 100 以上，30,000 元以下  
(B) 每人一事件新台幣 200 以上，20,000 元以下  
***(C) 每人一事件新台幣 500 以上，20,000 元以下***  
(D) 每人一事件新台幣 1,000 以上，30,000 元以下  

觀念釐清：
- 《個人資料保護法》第 28 條第 3 項：  
  依前二項情形，如被害人不易或不能證明其實際損害額時，得請求法院依侵害情節，以每人每一事件新臺幣五百元以上二萬元以下計算。

判斷規則：  
- 個資法無法證明實際損害金額 → 每人每一事件 `500～20,000 元`。

---
**在挑選以生物辨識（Biometrics）為主的驗證設備時，下列何種評估要素「不」是常用來比較設備間的優劣性？**  
(A) 錯誤接受率（False Acceptance Rate, FAR）  
***(B) 正確拒絕率（True Rejection Rate, TRR）***   
(C) 錯誤拒絕率（False Rejection Rate, FRR）  
(D) 交叉錯誤率（Crossover Error Rate, CER）  

觀念釐清：
- `TRR` 雖然概念上可對應「正確拒絕非本人」的比例，但不是生物辨識設備比較優劣時最常見的標準指標。

判斷規則：  
- 看到 `FAR` → 錯把壞人放進來，安全性問題。  
- 看到 `FRR` → 錯把本人擋在外面，便利性問題。  
- 看到 `CER / EER` → FAR 與 FRR 相等時的錯誤率，常用來比較整體辨識效果。
- 看到 `TRR` → 不是常用比較指標，本題選它。
