

# 1.���ݵ������룺

    1.����docker�е�mongo��
        docker exec -it docker_mongodb_1 bash
    2.�����ļ���
        ��ע�⣺
            �����鿴������
            mongodump --help 
        ��gzѹ���ļ���
            mongodump -h 127.0.0.1:27017 --archive=/home/agri.20191208.gz --gzip -d=agri
        ��BSON�ļ���
            mongodump -h 127.0.0.1:27017 -d agri -o /home/
        �����ͣ�
            -h ��ʾ host
            -d/--db ��ʾ database
            --archive ��ʾ���
            -o ��ʾ output directory
            --gzip ��ʾѹ��
            -u ��ʾ username
            -p ��ʾ password
    3.�����ļ�ȡ�ر��أ�
        docker cp docker_mongodb_1:/home/agri.20191208.gz ~/ mongodb-backup/
            docker_mongodb_1 ��ʾ������
            /home/agri.20191208.gz ����·��
            ~/mongodb-backup/ ��ʾ����·��
    4.���ݿ⵼�루Docker ��� MongoDB����
        2.1�����������ļ��� Docker ��� MogonDB
            sudo docker cp ~/mongodb-backup/agri.20191208.gz docker_mongodb_1:/home/
        2.2���ָ� gz ������ MongoDB
            mongorestore --gzip --archive=/home/agri.20191208.gz dump/ --dryRun --verbose
        --dryRun ��ʾ��ϰһ��
        --verbose ��ʾִ������
        ע��ȥ�� --dryRun --verbose ������Ļָ�����
   
# 2.ʾ����
    
    [root@centos ~]# docker exec -it 8b37 bash
    root@8b3794ffc91c:/# 
    root@8b3794ffc91c:/# mongodump --uri=mongodb://swen:swen123456@127.0.0.1:27017/app?authSource=admin --archive=/home/app.20191208.gz --gzip
    ... ʡ����־
    root@8b3794ffc91c:/# exit 
    exit
    [root@centos ~]# docker cp mongodb:/home/app.20191208.gz ./
    [root@centos ~]# scp app.20191208.gz root@118.25.13.144:/root
    
    //����Զ�̻�����
    [root@VM_0_9_centos ~]# docker cp app.20191208.gz mongodb2:/home
    [root@VM_0_9_centos ~]# docker exec -it mongodb2 bash
    root@8eccb1daf69c:/# mongorestore --uri=mongodb://swen:qwrq@@@#@127.0.0.1:27017/app?authSource=admin --archive=/home/app.20191208.gz dump/ --gzip
    //���ϻ򱨴�������������@
    ��ʾ�û�����������������֡��������ߡ�@���ַ�ʱ��������Ҫ���б��롣��ʵ����ܼ򵥣����ǳ��֣�����@����ʱ����������ַ���ʱ�ͻ�������⣬URL��ԭ���У���@�ַ�������û����������������Щ�ַ���
    ���޷�������Щ�������ķָ�����
    ����취��
        ��@ʹ��16���ƽ���URL���룺%40
        �ԣ�ʹ��16���ƽ���URL���룺%3A
        ������16���Ƶ�URL�������ԭ�����ַ������ˡ�
    root@8eccb1daf69c:/# mongorestore --uri=mongodb://swen:qwrq%40%40%40#@127.0.0.1:27017/app?authSource=admin --archive=/home/app.20191208.gz dump/ --gzip


