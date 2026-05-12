PostgreSQL18

```yaml
services:
  db:
    image: postgres:18
    volumes:
      # 親ディレクトリをマウントするのが今後のスタンダードらしい
      - ./postgres_data:/var/lib/postgresql
    environment:
        POSTGRES_USER: user
        POSTGRES_PASSWORD: password
        POSTGRES_DB: app
    ports:
      - "5432:5432"

volumes:
    postgres_data:

```