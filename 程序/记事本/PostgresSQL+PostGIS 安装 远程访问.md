# PostgresSQL+PostGIS 安装

## PostgresSQL 安装

1. 添加GPG密钥

   ~~~shell
   wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
   echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" |sudo tee  /etc/apt/sources.list.d/pgdg.list
   ~~~

2. 使用apt安装

   ~~~
   sudo apt -y install postgresql-12
   ~~~

   

3. 更改postgres密码

   ~~~
   alter user postgres with password 'password';
   ~~~

   

4. 远程访问

   ##### 1. 修改postgresql.conf

   `postgresql.conf`存放位置在`/etc/postgresql/12/main`下，这里的`x`取决于你安装PostgreSQL的版本号，编辑或添加下面一行，使PostgreSQL可以接受来自任意IP的连接请求。

   ```ini
   listen_addresses = '*'
   ```

   ##### 2. 修改pg_hba.conf

   `pg_hba.conf`，位置与`postgresql.conf`相同，虽然上面配置允许任意地址连接PostgreSQL，但是这在pg中还不够，我们还需在`pg_hba.conf`中配置服务端允许的认证方式。任意编辑器打开该文件，编辑或添加下面一行。

   ```ini
   # TYPE  DATABASE  USER  CIDR-ADDRESS  METHOD
   host  all  all 0.0.0.0/0 md5
   ```
## PostGIS 安装

1. 使用apt安装

   ~~~shell
   sudo apt -y install postgresql-12-postgis-3
   ~~~
2. 连接数据库

   ~~~
   psql -d 数据库名
   ~~~

   

3. 数据库添加扩展

   ~~~sql
   数据库名=# CREATE EXTENSION postgis;
   ~~~

   

4. 验证

   ~~~sql
   数据库名=# SELECT PostGIS_version();
   ~~~

   

