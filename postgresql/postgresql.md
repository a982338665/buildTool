
## 1.��װdocker��PostgreSQL
### 1.1��ȡָ���汾��PostgreSQL

    docker pull postgres:12.5

### 1.2����PostgreSQL����Ŀ¼

    mkdir -p /usr/local/pgdata

### 1.3����PostgreSQL

    docker run --name postgres -e POSTGRES_PASSWORD=123xxx56 \
     -p 5432:5432  -v /usr/local/pgdata:/var/lib/postgresql/data \
     -d postgres:12.5

### 1.4��װpsql�ͻ���

    wget https://download.postgresql.org/pub/repos/yum/9.3/redhat/rhel-7-x86_64/pgdg-centos93-9.3-3.noarch.rpm
    rpm -ivh pgdg-centos93-9.3-3.noarch.rpm
    yum install -y postgresql93

### 5. ʹ��psql�ͻ����������ݿ�
    
    psql -U postgres -d postgres -h 127.0.0.1 -p 5444
    Password for user postgres:
    psql (9.3.24)
    Type "help" for help.
 
### �����ʱ������ϣ������ͼ�ν���������Ͳ������ݿ⣬���Բ���pgadmin���ߣ��������棩��Ȼ����������з�����������5080�˿ڣ����ܴ�pgadmin��
    
    docker pull dpage/pgadmin4:4.17
    docker run --name pgadmin -p 5080:80 \
        -e 'PGADMIN_DEFAULT_EMAIL=pekkle@abc.com' \
        -e 'PGADMIN_DEFAULT_PASSWORD=xxxxxx' \
        -e 'PGADMIN_CONFIG_ENHANCED_COOKIE_PROTECTION=True' \
        -e 'PGADMIN_CONFIG_LOGIN_BANNER="Authorised users only!"' \
        -e 'PGADMIN_CONFIG_CONSOLE_LOG_LEVEL=10' \
        -d dpage/pgadmin4:4.17

### �鿴��sql

    �м������  
    1. �鿴��ʷ��SQL  
    ����Ҫ����log_min_duration_statement����¼��SQL��  
    Ȼ���ڲ���log_directory ָ����Ŀ¼�в鿴��־��  
        PostgreSQL ��־֧�ֵ������ʽ�� stderr��Ĭ�ϣ�, csvlog , syslog
        һ��Ĵ�����٣�ֻ���������ļ� ��postgresql.conf�������ü�����������Ȼ���д��󼶱��Ҫ���á�
        logging_collector = on
        log_destination = 'stderr'
        log_directory = 'log'
        log_filename = 'postgresql-%Y-%m-%d_%H%M%S.log'
        SELECT name,setting,vartype,boot_val,reset_val FROM pg_settings 
        where name in('logging_collector','log_destination','log_directory','log_filename');
        Ĭ�ϵĸ�����־��¼�� pgdate/log �У��� /usr/local/pgsql/data/log ��
        ����������Ҫ����˵����
        log_rotation_age = 1440                #minute,�೤ʱ�䴴���µ��ļ���¼��־��0 ��ʾ����չ��
        log_rotation_size = 10240            #kb,�ļ����󴴽��µ��ļ���¼��־��0 ��ʾ����չ��
        log_truncate_on_rotation = on         #������ͬ����־�ļ�
        ����Ҫ����SQL����������䣬����Ҫ�������²�����
        log_statement = all     #�����ø���������䣬����ֻ�ܸ��ٳ�����Ϣ
        log_min_duration_statement = 5000    #milliseconds,��¼ִ��5�뼰���ϵ����
        log_statement��
        ���ø��ٵ�������ͣ���4�����ͣ�none(Ĭ��), ddl, mod, all�������������ʱ������Ϊ "all"��
        log_min_duration_statement��
        ��������ѯ��䣬��λΪ���롣������ 5000����ʾ��־����¼ִ��5�����ϵ�SQL��䡣
        �� log_statement=all �� log_min_duration_statement ͬʱ����ʱ��������������䣬����log_min_duration_statement ���á������谴�����������һ��������ֵ��
    2. �鿴����ִ�е���SQL  
    �����ѯִ��ʱ�䳬��1���SQL  
    select * from pg_stat_activity where state<>'idle' and now()-query_start > interval '1 s' order by query_start ; 

    3.����Ĳ�ѯ
        select pid,usename,pg_blocking_pids(pid) as blocked_by,query as blocked_query from pg_stat_activity where cardinality(pg_blocking_pids(pid))> 0;

### Postgresql �鿴��ǰ�����������������
    
    �鿴���������
        show max_connections;
    �鿴������
        select count(*), usename from pg_stat_activity group by usename;
    ��ѯ������������ע���Ƿ����ǹر����ӡ� ���⻹���Բ鿴�������ǲ��ǹ�������⡣
        select count(*) from pg_stat_activity where state='idle'; 


    pg_cancel_backend() ȡ����̨�������ع�δ�ύ����
        select concat('select  pg_terminate_backend(',pid,');') from pg_stat_activity where datname='${databasename}'
        -- ��ȡ������ص�pid����ȡ����ز�����
        select  pg_terminate_backend(3802);
        select  pg_terminate_backend(20484);
        select  pg_terminate_backend(25389);
    -- ֱ��ȡ����̨����
        select pg_terminate_backend(pid) from  (select pid from pg_stat_activity where datname = '${databasename}') t;
    
    pg_stat_activity ����Ӧ��
    �������ͼ��򵥵��÷���ͳ�Ƶ�ǰ�ж��ٻ�Ծ�Ŀͻ���
        select count(*) from pg_stat_activity where not pid = pg_backend_pid();
    ������� ������ʱ�����û������������ max_connections �ж����
    �鿴һ����˽��������˶�ã��Լ�����ǰ�Ƿ��ڵȴ�
        select pid,state,CURRENT_TIMESTAMP - least(query_start,xact_start) AS runtime,
        substr(query,1,25) AS current_query
        from pg_stat_activity
        where not pid = pg_backend_pid();

## ��ѯ���Ա�����
    
    SELECT tablename FROM pg_tables WHERE tablename NOT LIKE 'pg%' AND tablename NOT LIKE 'sql_%' ORDER BY tablename;

