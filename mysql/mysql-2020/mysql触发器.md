
**1.MySQL�ָ�����DELIMITER����**
    
    DELIMITER $
    ... --������������䣻
    $   --�ύ������䣻
    DELIMITER ;

**2.������ֵ��**
    
    -- ����ֱ�Ӹ�ֵ
    set @num=999;
    -- ʹ��select����ѯ���������ݷ�ʽ��ֵ����Ҫ�����ţ�
    set @name =(select name from table);

**3.�����жϣ�**
    
    -- �򵥵�if��䣺
    set sex = if (new.sex=1, '��', 'Ů');
    -- ������if��䣺
    if old.type=1 then
        update table ...;
    elseif old.type=2 then
        update table ...;
    end if;

**4.�鿴��������**
    
    -- ͨ��information_schema.triggers��鿴��������
    select * from information_schema.triggers;
     
    -- mysql �鿴��ǰ���ݿ�Ĵ�����
    show triggers;
     
    -- mysql �鿴ָ�����ݿ�"aiezu"�Ĵ�����
    show triggers from aiezu;
    
**5.ɾ����������**
    
    1������ʹ��drop triggerɾ����������
    drop trigger trigger_name;
     
    2��ɾ��ǰ���ж�Ԥ���Ƿ���ڣ�
    drop trigger if exists trigger_name
   
**6.ʵ��1��**
    
    -- �������Ա�
    drop table if exists tmp1;
    create table tmp1 (n1 int, n2 int);
     
    -- ����������
    DELIMITER $
    drop trigger if exists tmp1_insert$
    create trigger tmp1_insert
    before insert on tmp1
    for each row
    begin
        set new.n2 = new.n1*5;
    end$
    DELIMITER ;
    
**7.ʵ��2��**

    -- �������Ա�Ͳ����������
    drop table if exists tmp1;
    drop table if exists tmp2;
    create table tmp1 (id int, name varchar(128)) default charset='utf8';
    create table tmp2 (fid int, name varchar(128)) default charset='utf8';
    insert into tmp1 values(1, '��E��');
    insert into tmp2 values(1, '��E��');
     
    -- ����������
    DELIMITER $
    drop trigger if exists tmp1_update$
    create trigger tmp1_update
    after update on tmp1
    for each row
    begin
        update tmp2 set name=new.name where fid=new.id;
    end$
    DELIMITER ; 

**3.ʵ��3��**
    
    DELIMITER $
    CREATE TRIGGER user_log AFTER INSERT ON users FOR EACH ROW
    BEGIN
    DECLARE s1 VARCHAR(40)character set utf8;
    DECLARE s2 VARCHAR(20) character set utf8;#���淢�������ַ�����������룬���������ַ���
    SET s2 = " is created";
    SET s1 = CONCAT(NEW.name,s2);     #����CONCAT���Խ��ַ�������
    INSERT INTO logs(log) values(s1);
    END $
    DELIMITER ;

**4.���ԣ�**
    
    ��һ��������һ����ʱ�� t (x,cc)
    
    �ڶ�����set global?general_log=on����������Ч����������mysql��
    
    ----�򿪺� general_log�� mysql ��Ѵ��������е�ÿһ��sql ���д�� ��־�ļ���?general_log_file?
    
    �Ϳ��Ը�����־���������ж�trigger ����һ���쳣û��ִ����ȥ��
    
    ####�����ԵĴ���������
    
    CREATE DEFINER=`root`@`%` TRIGGER `t_afterinsert_to_summary` AFTER INSERT ON `a` FOR EACH ROW ?
    begin
    declare v1 VARCHAR( 20 );
    declare v2 VARCHAR( 20 );
    declare done int default 0;?
    DECLARE?? ?mob VARCHAR ( 20 );
    DECLARE?? ?content VARCHAR ( 500 );
    DECLARE?? ?node_ip VARCHAR ( 20 );
    DECLARE mobile_list CURSOR FOR ?SELECT mobile FROM?? ?c ?WHERE?? ?c.c = ?new.c1;
    declare continue handler for not FOUND set done = 1; /*done = true;���*/
    
    
    insert into t (x,cc) ?? ?VALUES(?? ?new.c1,?? ?'topfirest0');-------��Ϊ������ҵ��
    IF ( new.c1 = 0 ) THEN
    ? insert into t (x,cc) ?? ?VALUES(?? ?new.c1,?? ?'firest1');-------��Ϊ������ҵ��
    ? select b into v1 from b where b.a=new.c1;
    ?? ?set v2=new.c1;
    ?? ?insert into t (x,cc) ?? ?VALUES(?? ?new.c1,?? ?'firest2');-------��Ϊ������ҵ��
    ?? ?SET content = CONCAT( 'abcabcabc', '[', v2, ']', 'dede', v2,'ccddddd' );
    ?? ?insert into t (x,cc) ?? ?VALUES(?? ?new.c1,?? ?'firest3');-------��Ϊ������ҵ��
    
    ?? ?insert into t (x,cc) ?? ?VALUES(?? ?new.c1,?? ?'firest4');-------��Ϊ������ҵ��
    ?? ?
    ?? ?OPEN mobile_list;-- ���α��е�ֵ��ֵ��������Ҫע��sql����е�˳��
    ?? ?REPEAT
    ?? ??? ?FETCH mobile_list INTO mob;-- whileѭ��
    ?? ??? ? ?if not done then
    ?? ??? ??? ??? ??? ?insert into t (x,cc) ?? ?VALUES(?? ?new.c1,?? ?'firest5');-------��Ϊ������ҵ��
    ?? ??? ??? ??? ??? ?INSERT INTO t (x,cc) ?? ?VALUES(?? ?v2,?? ?content);
    ?? ??? ? ?end if;
    ?? ??? ?-- �ر��α�
    ?? ??? ?until done end repeat;
    ?? ?CLOSE mobile_list;
    END IF;
    end;
