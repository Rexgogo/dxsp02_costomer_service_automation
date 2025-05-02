# n8n自動化平台部署技術說明
> Docker + n8n + Postgres + Nginx Proxy Manager

## 環境架構

- **n8n**: 開源的low-code工作流程自動化平台
- **PostgreSQL**: 資料儲存後端，用來儲存所有 n8n 的 workflow 定義、使用者帳號、執行歷史等持久性資料(採bind mount，儲存目標為./docker/postgres）
- **Nginx Proxy Manager**: 設定 HTTPS 網域、反向代理(Reverse Proxy)、憑證自動續期等功能

以**Docker Compose**進行服務佈佈屬，提供後續系統遷移彈性

```
[使用者]
   ↓  https://n8n.xxdomain.com
[Nginx Proxy Manager]
   ↓  反向代理 (Reverse Proxy) + HTTPS
     [n8n]
       ↓ 資料連線
     [PostgreSQL]
```

## Proxy setup 

1. visit http://localhost:81
2. login with default account
3. add proxy host
4. Domain Names: n8n.yourdomain.com
5. Scheme：​http
6. Forward Hostname / IP：​n8n（or n8n container name）
7. Forward Port：​5678（n8n default port） 
8. SSL: Request a new SSL Certificate
9. [x] FORCE SSL


![alt text](image.png)

## Debug
如果預設帳號無法登入
1. 停止 NPM 容器
2. 刪除容器資料夾的data rm -rf ./docker/npm/data
3. 重新啟動 NPM 容器

## 資安

| 機制 | 說明 |
|------|------|
| **HTTPS 憑證** | 由 NPM 使用 Let's Encrypt 自動申請與續期，保護資料傳輸加密。 |
| **Basic Auth 登入保護** | 限定管理者帳號登入 n8n UI。 |
| **容器隔離與網路分層** | n8n 與 Postgres 使用內部網路通訊，避免未授權外部存取。 |

## 維運事項

- 定期備份 PostgreSQL 資料夾（`./docker/postgres`）
- 檢查 NPM 憑證是否自動續期正常
