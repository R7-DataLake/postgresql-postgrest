create role admin nologin;
grant usage on schema libs to admin;

create role r7admin noinherit login password 'r7password';
grant admin to r7admin;
