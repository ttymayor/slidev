---
# try also 'default' to start simple
theme: default
# background: https://cover.sli.dev
author: tantuyu
title: 網頁漏洞入門
info: |
  ## 網頁漏洞入門
# class: text-center
drawings:
  persist: false
transition: slide-left
mdc: true
---

# 網頁漏洞入門

20251002 ． tantuyu

---

## 目錄

<Toc columns="2" />

---
transition: slide-up
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
<InputExample label="帳號" value="tantuyu" />
<InputExample label="密碼" value="12345678" />

<p class="text-red-400 !mb-0">系統提示：密碼錯誤</p>

::right-example::
系統提示：使用者名稱或密碼有誤。

或者可以再用 CAPTCHA 驗證或 2FA

---
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
