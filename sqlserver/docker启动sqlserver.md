

###1.���
    
    docker run --restart always -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=YourStrongP@SSW0RD' -e 
    'MSSQL_PID=Developer' -p 1433:1433 --name SQL_CONTAINER -d microsoft/mssql-server-linux

###2.���ͣ�
    
    --restart always -�����Ϊ�κ�ԭ��CONTAINER����ֹ���⽫�Զ�������������
    
    -e 'ACCEPT_EULA=Y' ����һ����������ʾ�����������û����Э�顣�������ͬ�⣬��װ�����������
    
    -e 'MSSQL_SA_PASSWORD=YourStrongP@SSW0RD' һ��Ҫ�ı�YourStrongP@SSW0RD �ڴ�������ΪSA�ʻ�ѡ�����롣���ȱ�������Ϊ8λ�����ұ������ٰ�������3��:��д(A-Z)��Сд(A-Z)������(0-9)��/�������ַ���
    
    -e 'MSSQL_PID=Developer'����һ��������ɺͲ�Ʒ��Կ�Ĳ����������Ժ� Evaluation, Developer, Express, Web, Standard, Enterprise ���� ##### - ##### - ##### - ##### - #####ʹ�á�(#����ĸ������)
    
    -p 1433:1433�˲���ָ���˿�ת������һ��1433ָ��Ҫ���ⲿʹ�õĶ˿ڣ��ڶ���1433ָ��Docker�еĶ˿ڡ�
    
    --name SQL_CONTAINER ָ��CONTAINER�����ơ�
    
    -d microsoft/mssql-server-linux һ��CONTAINER��ͼ�����û��ָ����Ĭ������£�������װ���°汾��

###3.ʹ�����

    docker run  -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=AAAAXXXx123' -e  'MSSQL_PID=Developer' -p 1433:1433 --name sqlserver -d microsoft/mssql-server-linux
    docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=AAAAXXXx123' \
     -p 1433:1433 --name mssql -v /data:/var/opt/mssql \
     -d mcr.microsoft.com/mssql/server:2017-latest

    -e 'ACCEPT_EULA=Y'	���ô˲���˵��ͬ�� SQL SERVER ʹ������ , �����޷�ʹ��
    -e 'SA_PASSWORD=����'	�˴����� SQL SERVER ���ݿ� SA �˺ŵ�����
    -p 1433:1433	�������� 1433 �˿�ӳ�䵽������ 1433 �˿�
    --name mssql	����������Ϊ mssql
    -v /data:/var/opt/mssql	y�������� /data ӳ�䵽���� /var/opt/mssql , ���㱸������
    �����������ý���
        �����������Զ���������
            --restart=always
        ��������·��ӳ����ߴ������ݾ�

###4.��¼���Ӳ��ԣ�
    
    �˺ţ�SA
    ���룺AAAAXXXx123

###5.����״̬��
    
    1.docker container ls --�鿴��������״̬
    2.�޸�SA���룺
        sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
           -S localhost -U SA -P '������' \
           -Q 'ALTER LOGIN SA WITH PASSWORD="������"'
    3.����sqlserver��
        1.docker exec -it mssql bash    --���������ڲ�
        2./opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P '���õ�sa����' --��½�ɹ�������
            >1
    4.������
        �������ݿ�
            ʹ������������Դ�����Ϊ TestDB �����ݿ�
            CREATE DATABASE TestDB
            ���������ѯ���е��������ݿ���
            SELECT Name from sys.Databases
            ����������������� , ʵ��û������ִ�� , ��������һ������ GO , ��ִ����������
            GO
        ��������
            ������Ϊ Inventory �ı�������������
            ѡ�����ݿ�
            USE TestDB
            ����
            CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
            ��������
            INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
            ִ������
            GO
        ��ѯ����
        
        ͨ�� sqlcmd �������������ѯ��������
        
        SELECT * FROM Inventory
        ִ��
        
        GO
        �˳� sqlcmd �����й���
        
        ʹ�� QUIT �����˳� sqlcmd
        
        
        QUIT
        
