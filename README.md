# 現場案件管理アプリ（MVP）

## 概要
- 管理Web + 作業員PWA（React）
- API（Node/Express でも Nest でもOK）
- DB: PostgreSQL
- 通知: FCM（Web Push）+ メール
- 写真: S3 直PUT

## 初回セットアップ
1) リポジトリ作成 → この README を配置  
2) `.env` を作成（`.env.example`を参考）  
3) `docker compose up -d` で DB／nginx／開発用コンテナ起動  
4) バックエンドでマイグレーション & 初期データ  
   ```bash
   make migrate
   make seed
5) フロント／バックエンド起動
   make be   # backend (http://localhost:3000)
   make fe   # frontend (http://localhost:5173)
6) ブラウザで http://localhost にアクセス（nginxがフロントへプロキシ）

# ディレクトリ
app/
  frontend/   # 管理Web + PWA
  backend/    # API + DBマイグレーション
  shared/     # 型・定数
  infra/      # Dockerfile/nginx/TF（後日）

# 開発の流れ（MVP）
  ・SP2: 認証 → 案件CRUD/検索/候補 → ステータス通知（既定ON） → 位置保存 → CSVプレビュー
　・SP3: レポート/CSV出力 → レイアウトD&D → 監査の可視化

# よく使うコマンド
  make up       # 起動
  make down     # 停止
  make migrate  # DBマイグレーション
  make seed     # 初期データ投入
  make be       # API起動（dev）
  make fe       # Front起動（dev）
