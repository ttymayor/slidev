---
# try also 'default' to start simple
theme: default
# background: https://cover.sli.dev
author: tantuyu
title: 入門網頁漏洞
info: |
  ## 入門網頁漏洞
# class: text-center
drawings:
  persist: false
transition: slide-left
mdc: true
---

# 入門網頁漏洞

20251002．tantuyu

---

## 目錄

<Toc columns="1" />

---
layout: tty-middle
transition: slide-up
---

## 極．入門

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

### F12 DevTool

瀏覽器內建的除錯 / 檢查工具

<Image src="./F12_DevTool_example.png" height="240" />

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

（在不同瀏覽器上可能有不同的名稱欄位）

- Elements
- Console
- Network
- Application
- Sources
- ...

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

你說...這東西對駭客有用？

<Image src="./Thinking.jpg" height="180" />

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

對，有用，可以說只要牽扯到網頁、工程師、開發、資料等，幾乎在這裡可以找到問題

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

最近有個例子「[鏟子英雄](https://shovel-heroes.com/)」被爆

> 「前端居然能直接改變後端狀態，還能執行一堆未授權操作，可以隨意完成/取消人力需求，以及 CRUD 開一下 F12 所有人的電話都直接現形了」 -- 擷取自 [Threads 文](https://www.threads.com/@jaja.rifuci/post/DPO9EkiEka7?xmt=AQF0XEtDCF4wTb34yGv_9hxY083rP0gvF6RXsW5dputgeg&slof=1)

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

題外話，另個 Vibe Coding 的慘況，[去你的，Google 這招太奸詐了！](https://www.facebook.com/lady1211christy/posts/pfbid0Yuz52ioNrh3FLYB6r1CmVnHsENs1EDYbKSDos7etSE3YEPSiD9sf5zstN4AFk2ysl?rdid=c1Y4PkkQgeoGVmwR)

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

我知道各位怕刪文，所以我截圖了

<Image src="./Damn_you_Google.png" height="320" />

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

幫各位總結，這篇原文簡單直白來說就是：直接把密碼寫在程式碼當中。

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

F12 中的常用功能：

<v-clicks>

- Elements 元素：網頁的內容，僅可在 Client 端修改
- Console 控制台：執行 JavaScript、查看錯誤訊息
- Network 網路：可以看到網頁請求了什麼、引入了什麼、API 呼叫
- Application 應用程式：可以看到 Cookie、Storage 等
- Sources 原始碼：瀏覽前端 JS 程式碼、下中斷點、逐行 Debug

</v-clicks>

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

### Cookie vs Storage 差異整理

| 特性        | Cookie       | LocalStorage | SessionStorage |
| --------- | ------------ | ------------ | -------------- |
| 容量        | 幾 KB         | ~5–10 MB     | ~5–10 MB       |
| 存活時間      | 可設定到期日       | 永久（直到刪除）     | 分頁關閉即刪除        |
| 是否隨請求自動送出 | ✅ 會          | ❌ 不會         | ❌ 不會           |
| 常見用途      | Session、登入狀態 | 偏好設定、大量暫存    | 臨時資料、單次流程      |

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

### 恕我快速帶過程式語言的基礎語法 ><

```js
// 算術
1 + 2, 5 - 3, 2 * 3, 10 / 2, 5 % 2

// 比較（注意 == 與 === 差別）
"5" == 5    // true （會型別轉換）
"5" === 5   // false（純比較型別與值）

// 邏輯
true && false, true || false, !true
```

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

```js
// 條件
if (x > 5) {
  console.log("big");
} else if (x === 5) {
  console.log("equal");
} else {
  console.log("small");
}

// 迴圈
for (let i=0; i<3; i++) console.log(i);

let i = 0;
while (i < 3) { console.log(i); i++; }
```

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

所以... 來幾題簡單的 picoCTF 吧

- [Inspect HTML](https://play.picoctf.org/practice/challenge/275?category=1&page=1)
- [Includes](https://play.picoctf.org/practice/challenge/274?category=1&page=1)
- [Insp3ct0r](https://play.picoctf.org/practice/challenge/18?category=1&page=2)

###### tag: `Web`

---
hideInToc: true
layout: tty-middle
transition: slide-up
---

再來幾題稍微動腦、需要 Google 或 AI 幫忙的吧

- [dont-use-client-side](https://play.picoctf.org/practice/challenge/66?category=1&page=2)
- [logon](https://play.picoctf.org/practice/challenge/46?category=1&page=2)
- [Scavenger Hunt](https://play.picoctf.org/practice/challenge/161?category=1&page=2)

###### tag: `Web`

---
transition: slide-up
layout: tty-middle
---

## OWASP Top 10

1. Broken Access Control (XSS)
2. Cryptographic Failures
3. Injection
4. Insecure Design
5. Security Misconfiguration
6. Vulnerable and Outdated Components
7. Identification and Authentication Failures
8. Software and Data Integrity Failures
9. Security Logging and Monitoring Failures
10. Server-Side Request Forgery (SSRF)

---
hideInToc: true
transition: slide-up
layout: tty-four-grid
---

### Broken Access Control (XSS) 權限控制失效

::top-left::
導致未經授權的用戶可以訪問敏感資料或功能，從而取得非預期提供的資訊。

::top-right::
防範方式：

- 嚴格限制存取權限。
- 定期測試存取控制規則。

::wrong-example::

```ts
https://example.com/userinfo/username=tantuyu
https://example.com/userinfo/username=admin
```

---
hideInToc: true
transition: slide-up
layout: tty-four-grid
---

### Cryptographic Failures 加密機制失效

::top-left::
敏感資料未正確加密，或使用不安全的加密方法。

::top-right::
防範方式：

- 使用當代強加密方法（如 AES 或 TLS 1.2/1.3）
- 避免硬編碼加密密鑰。

::wrong-example::

- 使用過時的加密演算法（如 MD5）
- 未加密的敏感數據傳輸。

::right-example::

```
密碼 -> 雜湊/加密 -> 資料庫
```

---
hideInToc: true
transition: slide-up
layout: tty-four-grid
---

### Injection 注入式攻擊

::top-left::
攻擊者透過未經驗證的輸入操縱查詢或指令（如 SQL injection、XSS 等）。

::top-right::
防範方式：

- 使用現代框架（如 React、Angular）自帶的防範機制，避免直接操作 DOM。
- 建立 HTML 的白名單標籤。
- 過濾並驗證用戶輸入。

::wrong-example::

```js
<script>alert(1);</script>
```

---
hideInToc: true
transition: slide-up
layout: tty-four-grid
---

### Insecure Design 不安全設計

::top-left::
應用程式架構或設計缺乏安全考量。

::top-right::
防範方式：

- 在設計階段進行安全審查。
- 採用安全架構模式。

::wrong-example::
<LoginExample username="tantuyu" password="123456" />

::right-example::
系統提示：使用者名稱或密碼有誤。

或者可以再用 CAPTCHA 驗證或 2FA

---
hideInToc: true
transition: slide-up
layout: tty-four-grid
---

### Security Misconfiguration 安全設定缺陷

::top-left::
不當的文件配置或任意權限使應用程式暴露在攻擊風險中。

::top-right::
防範方式：

- 關閉不必要的功能或服務。
- 定期檢查配置安全性。

::wrong-example::

```
https://example.com/.git
https://example.com/.env
https://example.com/access.log
https://example.com/.htaccess
```

::right-example::
敏感的配置內容都應該要避免公開，甚至能減少有這些敏感訊息都要盡量減少。也請勿將所有檔案權限改寫為 777

---
hideInToc: true
transition: slide-up
layout: tty-four-grid
---

### Vulnerable and Outdated Components 危險或過舊的元件

::top-left::
使用具有已知漏洞的第三方元件、框架或作業系統

::top-right::
防範方式：

- 定期更新依賴元件或系統。
- 使用漏洞掃描工具。

::wrong-example::

- Windows 7
- MySQL 5.5
- Node.js 10.x

::right-example::
使用現今最新最穩定的版本（LTS），因為過去版本不再進行維護，過去的版本漏洞只會越找越多。因此要經常更新套件並維護專案。

---
hideInToc: true
transition: slide-up
layout: tty-four-grid
---

### Identification and Authentication Failures 認證及驗證機制失效

::top-left::
使用者身分驗證或管理存在問題。

::top-right::
防範方式：

- 實現多因素認證
- 弱密碼檢查

::wrong-example::

- Token 暴露於 URL
- 弱密碼（12345678、qwertyuiop）
- 不能正確的失效 Session

::right-example::
使用強化過的密碼（如：至少一個特殊字元、大寫字母、數字）、使用 2FA、Passkey 等等，確保帳號是由帳號本人操作，以及有時限的 Session。

---
hideInToc: true
transition: slide-up
layout: tty-four-grid
---

### Software and Data Integrity Failures 軟體及資料完整性失效

::top-left::
未檢查軟體和資料的完整性，導致可能被惡意操縱。

::top-right::
防範方式：

- 驗證軟體更新的簽名證
- 確保 CI/CD 管道的安全性

::wrong-example::

- 使用不受信任的依賴套件
- 未使用安全協議或未對更新檔案進行簽名驗證
- 缺乏數據完整性保護

::right-example::

- 對使用的套件進行來源和版本檢查
- 使用數字簽名或哈希驗證數據和檔案的完整性
- 對數據做加密檢查驗證

---
hideInToc: true
transition: slide-up
layout: tty-four-grid
---

### Security Logging and Monitoring Failures 資安記錄及監控失效

::top-left::
缺乏適當的日誌記錄和監控，無法及時發現和回應攻擊。

::top-right::
防範方式：

- 設置集中式日誌管理。
- 定期審查安全日誌。

::wrong-example::

- 無 Log 檔紀錄
- 日誌內容資訊缺漏
- 日誌保存時間過短

::right-example::

- 對任意操作都記錄到日誌上
- 將重要資訊都寫進日誌（IP、操作、日期等）
- 依法保存日誌時限

---
hideInToc: true
transition: slide-up
layout: tty-four-grid
---

### Server-Side Request Forgery (SSRF) 伺服器端請求偽造

::top-left::
攻擊者誘使伺服器向未經授權的目的地發出請求。

::top-right::
防範方式：

- 定期檢查所有目錄及 API 權限
- 使用安全代理來處理外部請求

---

主要攻擊原理

<Image src="./SSRF_example.png" height="420" />

---
transition: slide-up
layout: tty-middle
---

## 網頁漏洞那麼多，到底怎麼戳戳漏洞？

---
hideInToc: true
transition: slide-up
layout: tty-middle
---

### 工具和情報不能少

- [ZeroDay](https://zeroday.hitcon.org/)
- [CVE](https://www.cve.org/)
- [CWE](https://cwe.mitre.org/)
- [Wappalyzer](https://www.wappalyzer.com/) [(Chrome Extension)](https://chromewebstore.google.com/detail/wappalyzer-technology-pro/gppongmhjkpfnbhagpmjfkannfbllamg)

---
hideInToc: true
transition: slide-up
layout: tty-middle
---

### ZeroDay Example

1. [台灣工業與應用數學會 Vite 任意檔案讀取漏洞](https://zeroday.hitcon.org/vulnerability/ZD-2025-01167)
2. [ischool 澔學學習股份有限公司 存取控制缺陷](https://zeroday.hitcon.org/vulnerability/ZD-2025-01171)

---
hideInToc: true
layout: tty-middle
---

### CWE vs CVE

CWE 可以理解為類別

CVE 可以理解為實例

- [CWE-79 (XSS)](https://cwe.mitre.org/data/definitions/79.html)
- [CWE-89 (SQL Injection)](https://cwe.mitre.org/data/definitions/89.html)
- [CVE-2024-49038](https://www.cve.org/CVERecord?id=CVE-2024-49038)
- [CVE-2023-32530](https://www.cve.org/CVERecord?id=CVE-2023-32530)

---
transition: slide-up
layout: tty-middle
---

## 攻擊

> 拜託別亂打、會出事
> 
> ~~要打請先事先告知（或掛 VPN、跳板）~~

---
hideInToc: true
transition: slide-up
layout: tty-middle
---

### XSS Example

```html
<script>alert("XSS success")</script>
```

```html
<q onmouseover=alert(1)>鼠標移過我</q>
```

```html
<svg onload=alert(1)>
```

---
hideInToc: true
transition: slide-up
layout: tty-middle
---

### SQL Injection Example

先來認識 SQL 是什麼

> SQL（Structured Query Language，結構化查詢語言）是一種**用來和資料庫溝通的語言**。 -- ChatGPT

---
hideInToc: true
transition: slide-up
layout: tty-middle
---

獲取所有使用者（user）

```sql
SELECT * FROM users;
```

獲取所有使用者（user），條件是當 id=1 時

```sql
SELECT * FROM users WHERE id=1;
```

獲取所有使用者（user），條件是當 id=1 且 username="tantuyu"

```sql
SELECT * FROM users WHERE id=1 AND username="tantuyu";
```

新增一個使用者 username 為 tantuyu，密碼為 tantuyu

```sql
INSERT INTO users (username, password) VALUES ("tantuyu", "tantuyu");
```

---
hideInToc: true
transition: slide-up
layout: tty-middle
---

假設後端是 Python，以

```py
sql = f"SELECT * FROM users WHERE username = '{input_username}' AND password = '{input_password}';"
cur.execute(sql)
rows = cur.fetchall()
```
