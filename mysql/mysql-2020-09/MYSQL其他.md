
## ���ݿ���INFORMATION_SCHEMA��˵����ʹ��

    ��һ����ѯ���������ж��ٸ���������
    select * from INFORMATION_SCHEMA.TABLES
    information_schema�������ݱ�����MySQL�������������ݿ����Ϣ�������ݿ��������ݿ�ı��������������������Ȩ�޵ȡ��ټ򵥵㣬��̨MySQL�������ϣ���������Щ���ݿ⡢
        �������ݿ�����Щ��ÿ�ű���ֶ�������ʲô���������ݿ�ҪʲôȨ�޲��ܷ��ʣ��ȵ���Ϣ��������information_schema�����档
    Mysql��INFORMATION_SCHEMA���ݿ������һЩ�����ͼ���ṩ�˷������ݿ�Ԫ���ݵķ�ʽ��
    Ԫ�����ǹ������ݵ����ݣ������ݿ�����������е��������ͣ������Ȩ�޵ȡ���Щʱ�����ڱ�������Ϣ������������������ݴʵ䡱�͡�ϵͳĿ¼����
    
    �����һЩ��Ҫ�������ֵ����һЩ˵����
    SCHEMATA���ṩ�˹������ݿ����Ϣ��
    TABLES�������˹������ݿ��еı����Ϣ��
    COLUMNS�������˱��е�����Ϣ��
    STATISTICS�������˹��ڱ���������Ϣ��
    USER_PRIVILEGES�������˹���ȫ��Ȩ�޵���Ϣ������ϢԴ��mysql.user��Ȩ��
    SCHEMA_PRIVILEGES�������˹��ڷ��������ݿ⣩Ȩ�޵���Ϣ������Ϣ����mysql.db��Ȩ��
    TABLE_PRIVILEGES�������˹��ڱ�Ȩ�޵���Ϣ������ϢԴ��mysql.tables_priv��Ȩ��
    COLUMN_PRIVILEGES�������˹�����Ȩ�޵���Ϣ������ϢԴ��mysql.columns_priv��Ȩ��
    CHARACTER_SETS���ṩ�˹��ڿ����ַ�������Ϣ��
    COLLATIONS���ṩ�˹��ڸ��ַ����Ķ�����Ϣ��
    COLLATION_CHARACTER_SET_APPLICABILITY��ָ���˿�����У�Ե��ַ�����
    TABLE_CONSTRAINTS�������˴���Լ���ı�
    KEY_COLUMN_USAGE�������˾���Լ���ļ��С�
    ROUTINES���ṩ�˹��ڴ洢�ӳ��򣨴洢����ͺ���������Ϣ����ʱ��ROUTINES�������Զ��庯����UDF����
    VIEWS�������˹������ݿ��е���ͼ����Ϣ��
    TRIGGERS���ṩ�˹��ڴ����������Ϣ��

## 1. ��ȡ��������Ϣ(COLUMNS)
   
       SELECT  *  FROM information_schema.COLUMNS WHERE  TABLE_SCHEMA='���ݿ���';  COLUMNS���ṩ�˹��ڱ��е��е���Ϣ����ϸ������ĳ���������ĸ������ֶ�˵������:
        
       �ֶ�	����
       table_schema 	�������ߣ�����schema�����ƣ�
       table_name 	����
       column_name 	����
       ordinal_position 	�б�ʶ��
       column_default 	�е�Ĭ��ֵ
       is_nullable 	�е�Ϊ���ԡ���������� null����ô���з��� yes�����򣬷��� no
       data_type 	ϵͳ�ṩ����������
       character_maximum_length	���ַ�Ϊ��λ����󳤶ȣ����ڶ��������ݡ��ַ����ݣ������ı���ͼ�����ݡ����򣬷��� null���йظ�����Ϣ����μ���������
       character_octet_length 	���ֽ�Ϊ��λ����󳤶ȣ����ڶ��������ݡ��ַ����ݣ������ı���ͼ�����ݡ����򣬷��� nu
       numeric_precision 	�����������ݡ���ȷ�������ݡ��������ݻ�������ݵľ��ȡ����򣬷��� null
       numeric_precision_radix 	�����������ݡ���ȷ�������ݡ��������ݻ�������ݵľ��Ȼ��������򣬷��� null
       numeric_scale 	�����������ݡ���ȷ�������ݡ��������ݻ�������ݵ�С��λ�������򣬷��� null
       datetime_precision 	datetime �� sql-92 interval �������͵������ʹ��롣���������������ͣ����� null
       character_set_catalog 	��������ַ����ݻ� text �������ͣ���ô���� master��ָ���ַ������ڵ����ݿ⡣���򣬷��� null
       character_set_schema 	��������ַ����ݻ� text �������ͣ���ô���� dbo��ָ���ַ��������������ơ����򣬷��� null
       character_set_name 	����������ַ����ݻ� text �������ͣ���ôΪ�ַ�������Ψһ�����ơ����򣬷��� null
       collation_catalog 	��������ַ����ݻ� text �������ͣ���ô���� master��ָ�������ж��������������ݿ⡣�������Ϊ null
       collation_schema 	���� dbo��Ϊ�ַ����ݻ� text ��������ָ���������������ߡ����򣬷��� null
       collation_name 	��������ַ����ݻ� text �������ͣ���ôΪ������򷵻�Ψһ�����ơ����򣬷��� null��
       domain_catalog 	�������һ���û������������ͣ���ô������ĳ�����ݿ����ƣ��ڸ����ݿ����д����������û������������͡����򣬷��� null
       domain_schema 	�������һ���û������������ͣ���ô�����������û������������͵Ĵ����ߡ����򣬷��� null
       domain_name 	�������һ���û������������ͣ���ô�����������û������������͵����ơ����򣬷��� NULL

## information_schema.columns�ֶ�˵������ȡ���ݿ����������Ϣ
    
    MySQL�汾����5.0ʱ���и�Ĭ�����ݿ�information_schema�����������������ݿ����Ϣ(��������� ��������ӦȨ�޵�)��ͨ��������ݿ⣬���ǾͿ��Կ���ѯ�������С�
    
     
    
    ��ȡ��������Ϣ(COLUMNS)
    
    SELECT  *  FROM information_schema.COLUMNS WHERE  TABLE_SCHEMA='���ݿ���';  COLUMNS���ṩ�˹��ڱ��е��е���Ϣ����ϸ������ĳ���������ĸ������ֶ�˵������:
    
     
    
    ��Ҫ����Щ��ͼ�м�����Ϣ����ָ����ȫ�ϸ�� INFORMATION_SCHEMA view_name ���ơ�
    
     
    
    ����	��������	����
    TABLE_CATALOG	nvarchar(128)	���޶�����
    TABLE_SCHEMA	nvarchar(128)	�������ߡ�
    TABLE_NAME	nvarchar(128)	������
    COLUMN_NAME	nvarchar(128)	������
    ORDINAL_POSITION	smallint	�б�ʶ�š�
    COLUMN_DEFAULT	nvarchar(4000)	�е�Ĭ��ֵ��
    IS_NULLABLE	varchar(3)	�е�Ϊ���ԡ���������� NULL����ô���з��� YES�����򣬷��� NO��
    DATA_TYPE	nvarchar(128)	ϵͳ�ṩ���������͡�
    CHARACTER_MAXIMUM_LENGTH	smallint	���ַ�Ϊ��λ����󳤶ȣ����ڶ��������ݡ��ַ����ݣ������ı���ͼ�����ݡ����򣬷��� NULL���йظ�����Ϣ����μ��������͡�
    CHARACTER_OCTET_LENGTH	smallint	���ֽ�Ϊ��λ����󳤶ȣ����ڶ��������ݡ��ַ����ݣ������ı���ͼ�����ݡ����򣬷��� NULL��
    NUMERIC_PRECISION	tinyint	�����������ݡ���ȷ�������ݡ��������ݻ�������ݵľ��ȡ����򣬷��� NULL��
    NUMERIC_PRECISION_RADIX	smallint	�����������ݡ���ȷ�������ݡ��������ݻ�������ݵľ��Ȼ��������򣬷��� NULL��
    NUMERIC_SCALE	tinyint	�����������ݡ���ȷ�������ݡ��������ݻ�������ݵ�С��λ�������򣬷��� NULL��
    DATETIME_PRECISION	smallint	datetime �� SQL-92 interval �������͵������ʹ��롣���������������ͣ����� NULL��
    CHARACTER_SET_CATALOG	varchar(6)	��������ַ����ݻ� text �������ͣ���ô���� master��ָ���ַ������ڵ����ݿ⡣���򣬷��� NULL��
    CHARACTER_SET_SCHEMA	varchar(3)	��������ַ����ݻ� text �������ͣ���ô���� DBO��ָ���ַ��������������ơ����򣬷��� NULL��
    CHARACTER_SET_NAME	nvarchar(128)	����������ַ����ݻ� text �������ͣ���ôΪ�ַ�������Ψһ�����ơ����򣬷��� NULL��
    COLLATION_CATALOG	varchar(6)	��������ַ����ݻ� text �������ͣ���ô���� master��ָ�������ж��������������ݿ⡣�������Ϊ NULL��
    COLLATION_SCHEMA	varchar(3)	���� DBO��Ϊ�ַ����ݻ� text ��������ָ���������������ߡ����򣬷��� NULL��
    COLLATION_NAME	nvarchar(128)	��������ַ����ݻ� text �������ͣ���ôΪ������򷵻�Ψһ�����ơ����򣬷��� NULL��
    DOMAIN_CATALOG	nvarchar(128)	�������һ���û������������ͣ���ô������ĳ�����ݿ����ƣ��ڸ����ݿ����д����������û������������͡����򣬷��� NULL��
    DOMAIN_SCHEMA	nvarchar(128)	�������һ���û������������ͣ���ô�����������û������������͵Ĵ����ߡ����򣬷��� NULL��
    DOMAIN_NAME	nvarchar(128)	
    �������һ���û������������ͣ���ô�����������û������������͵����ơ����򣬷��� NULL��
    
    ���Ƚ���һ�µ��Ǳ���
    select SCHEMA_NAME from information_schema.SCHEMATA  limit 5,1/* 5,1��ʾ�ӵ�1����ʼ��������5��
    Ȼ����Ǳ����ˡ�
    select TABLE_NAME from information_schema.TABLES  where  TABLE_SCHEMA=0��6D656D626572 limit 5,1/*TABLE_SCHEMA=�����ǿ�����16����
    �������ֶ�
    select COLUMN_NAME  from information_schema.COLUMNS  where TABLE_NAME=0��61646D5F75736572 limit 5,1/*
    
    �������ݶ��Ǵ�information_schema.columns��������ȡ����Ϊ��information_schema��������ǿ��Կ�������information_schema.columns���������ǿ��Բ鵽���е���Ϣ����Ϊ�������棬table_schema�� table_name��column_name��������ж��У��������ǿ���ֱ��ͨ����������������Ҫ��������Ϣ����ʡ�˻�����һ���ˣ���һ�������ٶ�
    
    SELECT
        TABLE_SCHEMA AS '���ݿ�',
        TABLE_NAME AS '����',
        column_name AS '�ֶ�����',
        COLUMN_TYPE AS '�ֶ�����',
        IS_NULLABLE AS '�Ƿ�Ϊ��',
       COLUMN_DEFAULT AS 'Ĭ��ֵ',
       column_comment AS '�ֶα�ע'
    FROM
       information_schema. COLUMNS
    WHERE
        table_name = 'yyd_elife_city'
    OR table_name = 'yyd_elife_column_list'
    OR table_name = 'yyd_elife_coupon_list'
    OR table_name = 'yyd_elife_goods_label_list'
    OR table_name = 'yyd_elife_member_extend'
    OR table_name = 'yyd_biz_content_log'
    OR table_name = 'yyd_e_refund'
    OR table_name = 'yyd_e_statistic_goods'
    OR table_name = 'yyd_e_statistic_ip'
    OR table_name = 'yyd_e_statistic_main'

## �鿴�������
    
    desc INFORMATION_SCHEMA.COLUMNS;
    
    table_catalog	varchar(512)
    table_schema	varchar(64)
    table_name	varchar(64)
    column_name	varchar(64)
    ordinal_position	bigint(21) unsigned
    column_default	longtext
    is_nullable	varchar(3)
    data_type	varchar(64)
    character_maximum_length	bigint(21) unsigned
    character_octet_length	bigint(21) unsigned
    numeric_precision	bigint(21) unsigned
    numeric_scale	bigint(21) unsigned
    datetime_precision	bigint(21) unsigned
    character_set_name	varchar(32)
    collation_name	varchar(32)
    column_type	longtext
    column_key	varchar(3)
    extra	varchar(30)
    privileges	varchar(80)
    column_comment	varchar(1024)
    generation_expression	longtext
