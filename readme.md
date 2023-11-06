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
grant usage on schema libs to admin;

create role r7admin noinherit login password 'r7password';
grant admin to r7admin;
```

Sign jwt with `role` key in payload

```json
{
  "role": "admin"
}
```

Using api

```shell
curl --request GET \
  --url http://localhost:8888/api/tableName \
  --header 'Authorization: Bearer ___JWT___'
```