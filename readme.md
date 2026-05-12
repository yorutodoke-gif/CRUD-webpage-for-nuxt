# CRUDウェブページ

DB ポストグレ

|ID|メッセージ|
|-|-|
|UUID|String Max 50文字 型任された|

ORM プリズマ
BackEnd nitro
Frontend nuxt.js

DBはマイグレーション

注意 データベースはスキップする

---

## パッケージメモ

### dependencies

絶対に必要なもの

```bash
pnpm add @prisma/client @prisma/adapter-pg pg dotenv
```

### devDependencies

開発時だけ必要

```bash
pnpm add -D prisma tsx @types/node
```

| モジュール | 意味 |
| --- | --- |
| prisma | CLI |
| @prisma/client | ORM |
| @prisma/adapter-pg | Postgres adapter |
| pg | PostgreSQL driver |
| dotenv | env |
| tsx | TS script実行 |

---

## 内部設計メモ

### Nuxt

### DB

```directory

prisma.config.ts  #DB.envを参照するように設定

DB.env  #データベースまでのURL

DB
└── prisma
    ├── generated       #DB設計図
    ├── migrations      #DB変更履歴
    └── schema.prisma   #Prisma自動生成コード
```
