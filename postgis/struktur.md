1. install postgresql dan postgis  
2. create new user from default superuser postgres  
3. create db in new user [createdb –U postgres Real-State]  
4. create extension postgis in new db [psql –d Real-State –U postgres] [CREATE EXTENSION postgis;]  
5. create scheme in new db  
6. create table in new scheme (upload file shp. One Shape File = One PostGIS Table)