### MySql报错： You can't specify target table 'table name' for update in FROM clause ###

在Mysql下执行：
	
	delete   from   blur_article    where   id   not   in(select   min(id)   from  blur_article    group   by   title)

用途是去重复标题，但是却报错！

	#1093 - You can't specify target table 'blur_article' for update in FROM clause 

在Mysql下执行：

	select *   from   blur_article    where   id   not   in(select   min(id)   from  blur_article    group   by   title)
执行查询语句却显示成功！

怎么回事呀，如果上面的delete不能执行，有没有别的sql可以做这样的操作？
我是想做一个去重复操作，比如说：

	字段          id       title   
	              1           张三   
	              2           李四   
	              3           张三   
	              4           王五   
	              5           李四   

最终结果是   

	              id       title   
	              1         张三   
	              2         李四   
	              4         王五

为什么呢?

mysql中不能这么用。 （等待mysql升级吧）

错误提示就是说，不能先select出同一表中的某些值，再update这个表(在同一语句中) 

替换方案：
 
	create table tmp as select min(id) as col1 from blur_article group by title;
	delete from blur_article where id not in (select col1 from tmp); 
	drop table tmp;

已经测试，尽请使用!
