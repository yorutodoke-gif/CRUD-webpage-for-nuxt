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

### pnpmはインストール時にscriptは止めてくれる安心設計！だけどprismaやnuxtでは許可しないといけない

```bash
pnpm approve-builds
```

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

├── app
│   └── app.vue
├── generated/ #Nuxt(server) が使う TypeScript client、実際使うのはserver/apiやserver/utils/db.ts側だからnuxtに配置
├── public
│   ├── favicon.ico
│   └── robots.txt
├── server
│   └── utils
│       └── db.ts
├── nuxt.config.ts
├── package.json
├── pnpm-lock.yaml
├── pnpm-workspace.yaml
├── README.md
└── tsconfig.json

### DB

```directory

prisma.config.ts  #DB.envを参照するように設定

DB.env  #データベースまでのURL

DB
└── prisma
    ├── migrations      #DB変更履歴
    └── schema.prisma   #Prisma自動生成コード
```

### pnpm-workspace.yaml

rootでもpnpm操作ができる用にしたもの、package.jsonにはCRUD-nuxtのpackage.jsonを読み込むように設定している