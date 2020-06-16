
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
