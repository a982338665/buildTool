

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
