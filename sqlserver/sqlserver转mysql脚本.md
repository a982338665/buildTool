### ��Դ��https://www.cnblogs.com/xinysu/p/6992415.html?utm_source=itdadao&utm_medium=referral

**1.ǰ�ԣ�**

    SQL SERVER�ı�ṹ������ת��ΪMySQL�ı�ṹ����������ʵ�ںܶ���������������ṩ������navicat��sqlyog�ȣ����ǣ��ڴ���ĳЩ�������͡�Ĭ��ֵ������ת����ʱ��
    ����Щ�������Ⲣ����Ҫ��װ��������˿�ʼ�뷨�ӣ����Ի���SQL SERVER��д��һ���洢���̣����Ը��ݱ���ֱ��ת��ΪMySQL�Ľ���������SQL�ű�
    ����� MySQL Innodb���棩��Ŀǰ��֧�ַ�����ķ������ü������������͵�ת����
    
**2.��������ת��**

    1.ת�����죺
        ����������ת��������±���Щ�������͵�ת��Ŀǰ�Ѳ��Թ�����������ʹ�á�
            ����ע���������ݿ�洢���ݵ�һЩ���죬�����ܷ���ܣ�
        ��SQL SERVER�е�datetime��������΢��(���С����3λ)����mysql���������룬ת�����Ƿ��Ӱ��ҵ�����Ӱ�죬��Ҫ����һ���ֶ�ר�����洢΢����ߺ��룬
            ��Ȼmysql��û��ʱ���������͵ľ��ȵ���΢����ߺ��룬����mysql�ṩ��΢�����ش�����microsecond��extract��date_format��
        ��MySQLʹ��tinyint����SQL SERVER��bit
        ��SQL SERVER��money����ʹ��decimal���
        ��timestamp��ת����SQL SERVER����һ��16���Ƶ����֣�����ʱ�����ÿ���޸Ķ�����ֵ������
        ���ӹ��ܿ��ǣ�ת��Ϊmysql��ʱ�򣬴���Ϊtimestamp���������ͣ�Ĭ��ֵΪCURRENT_TIMESTAMP���з����޸���ʱ�޸���һ�����ݣ��������ת������ô��SQL SERVER�������ݵ�ʱ�򣬾�Ҫ��Ӧ���������Ĵ洢����Ĭ����ô����
        �������ݿ��ǣ�ת��Ϊmysql��ʱ�򣬴���Ϊbigint���������ͣ��޸Ĵ洢����case when b.name = 'timestamp' then ' timestamp DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP ' Ϊcase when b.name = 'timestamp' then ' bigint ' ��
            ��������mysql����������������ֵ������ʵ��ͳһ�ģ�����ÿ�����̬�޸ģ�����������ת���Ĺ����У�Ϊauto_increment������ʵ��������������

  |ID|SQL SERVER	|MySQL	|Description|
  |----|----|----|----|
 |1	|bigint|bigint	 
 |2	|binary|binary	 
 |3	|bit   |tinyint	|SQL SERVER��bit���ͣ������㣬ʶ��ΪFalse������ֵʶ��ΪTrue��MySQL��û��ָ����bool���ͣ�һ�㶼ʹ��tinyint������
 |4	|char  |char	 
 |5	|date  |date	 
 |6	|datetime	|datetime	|ע�⣬mssql�ı�����΢��(���С����3λ)����mysql����������
 |7	|datetime2	|datetime	|ע�⣬mssql�ı�����΢��(���С����7λ)����mysql����������
 |8	|datetimeoffset	|datetime	|ע�⣬mssql�ı���ʱ���������Ҫ�����Լ�ת��mssql�ı�����΢��(���С����7λ)����mysql����������
 |9	|decimal	|decimal	 
 |10|	float	|float	 
 |11|	int	    |int	 
 |12|	money	|float	|Ĭ��ת��Ϊdecimal(19,4)
 |13|	nchar	|char	|SQL SERVERתMySQL�������ֽ���ת�Ϳ���
 |14|	ntext	|text	 
 |15|	numeric	|decimal	 
 |16|	nvarchar	|varchar	 
 |17|	real	|float	 
 |18|	smalldatetime	|datetime	 
 |19|	smallint	|smallint	 
 |20|	smallmoney	|float	|Ĭ��ת��Ϊdecimal(10,4)
 |21|	text	|text	 
 |22|	time	|time	|ע�⣬mssql�ı��������С����8λ����mysql����������
 |23|	timestamp	|timestamp	|ע�⣬mssql����ʱ���������Ϊmysql�� timestamp DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP �����Ժ��浼�������Ӱ�죬�ӹ��ܷ������������԰�������ת�����������������������Ҫת��16���Ƶ����ִ洢��mysql�У�����������Ϊbigint���ɣ��ڱ���е���ʱ�������á�
 |24|	tinyint	|tinyint	 
 |25|	uniqueidentifier	|varchar(40)	|��Ӧmysql��UUID(),����Ϊ�ı����ͼ��ɡ�
 |26|	varbinary	|varbinary	 
 |27|	varchar	|varchar	 
 |28|	xml	|text	|mysql��֧��xml���޸�Ϊtext
 
 **3.��������**
    
    1.MySQL��֧�ַ������ľۼ�������Ҳ���Ǿۼ�������������������ת���Ĺ����У������Ǹ���SQL SERVER����еľۼ�������ת���ġ�
    2.���룺
        --SQL SERVER���ݾۼ������������������mysql������
        SELECT
               col_name(i.object_id,ik.column_id) pk_col
        FROM sys.indexes i
        JOIN sys.index_columns ik ON i.index_id=ik.index_id and i.object_id=ik.object_id
        WHERE i.type=1
              and i.object_id=object_id('tb')
        ORDER BY key_ordinal
        
 **4.������ӣ�**
    
    ���ھۼ������Ѵ������Ϊ�������ڽ����SQL�����жϣ�������ֻ����Ǿۼ�������
    ���������ע�⣺
    MySQL��֧��INCLUDEѡ��İ��������������ڴ���Ĺ����У�INCLUDE����ӵ���������
    MySQL ��֧��WHEREѡ��Ĺ��������������ڴ���Ĺ����У�WHEREѡ��ȥ��
    �������ִ���������1-2���ģ�ֱ��IX_����������3���еģ�ȡÿ��ǰ3���ַ����������������Ȳ�����64���ַ���������ȡǰ64���ַ�
 
 
 **5.�洢���̣���D:\git-20191022\buildTool\sqlserver\convert.sql**
 **6.���ԣ�**
 
    --1.���������±�
        CREATE TABLE tbtest(
        id INT IDENTITY(1,1) NOT NULL ,
        name NVARCHAR(50) NOT NULL,
        phone VARCHAR(11) NOT NULL,
        age int default 99 ,
        birthday datetime default getdate(),
        addresss text,
        monyes money default 123456789012345.1234,
        smonyes smallmoney,
        nums int default 2,
        moneys money,
        smo smallmoney,
        curversion timestamp
        )
         
        ALTER TABLE tbtest ADD CONSTRAINT PK_tbtest PRIMARY KEY (ID,phone);
        CREATE INDEX IX_NAME ON tbtest(NAME);
        CREATE INDEX IX_phone_age ON tbtest(phone,age);
        CREATE INDEX IX_nums ON tbtest(nums) WHERE nums>2;
        CREATE INDEX IX_birthday ON tbtest(birthday) include (name,phone);
    2.ִ�У�exec p_tb_mssqltomysql 'tbtest' -- tbtestΪ����

 
 
 
 
