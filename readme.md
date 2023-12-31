PostgreSQL and PostgREST server

running:
```shell
docker compose up --force-recreate
docker compose up -d --force-recreate
```

API Endpoint `http://localhost:8888/api`

Create role:

```sql
create role admin nologin;
grant all on database r7platform to admin;

create role r7admin noinherit login password 'r7password';
grant admin to r7admin;
```

Sign jwt with `role` key in payload

```json
{
  "role": "admin"
}
```

Enable `safeupdate`

```sql
ALTER DATABASE r7platform SET session_preload_libraries = 'safeupdate';
```

Using api

```shell
curl --request GET \
  --url http://localhost:8888/api/tableName \
  --header 'Authorization: Bearer ___JWT___'
```