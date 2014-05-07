##MYSQL delete 语句别名 ##

	delete from table t where t.id = 123; (执行错误)
	
	select t.* from table t where t.id = 123; （执行正确）

### 原因： ###
Mysql 中 delete 在删除操作一张表的时候 不用别名操作成功！

### 正确的语句 ###
	delete from table where id = 123;
	或
	delete t from table t where t.id=123;