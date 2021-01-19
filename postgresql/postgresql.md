
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
 
