

## 1.������ܣ�����CP����
    
    scp file_name_to_copy username @ destination_host��destination_directory_path
    
    1.��һ���ļ��ӱ��ؼ�������Ƶ�Զ������
        scp Hello.scp tuts@192.168.83.132:/home
        �س���������
    2.���ƶ��ļ�:hello1,2,3
        scp Hello1 Hello2 Hello3 tuts@192.168.83.132:/home
    3.�ݹ鸴��Ŀ¼��
        scp -r FOSSTUTS tuts@192.168.83.132:/home
    4.�����ļ��Ҵ�ӡ���ƹ��̵���־    
        scp -v Hello1 Hello2 Hello3 tuts@192.168.83.132:/home
    5.������Զ������֮�临���ļ�
        scp tuts@192.168.43.96:/home/Hello1 tuts@192.168.83.132:/home/Hello1
    6.ѹ���͸����ļ�:Ϊ�˼ӿ츴�ƹ��̲���ʡ��������ʹ��-C����ѹ���ļ������ݽ��ڱ��ؼ�����ϼ�ʱѹ��������Զ�������Ͻ�ѹ������μ�������﷨��
        scp -vC Hello1 tuts@192.168.83.132:/home
    7.������ָ���������ļ����Ƶ�Զ���������Խ���Ϊ���ء�����ϴ�����ܸߣ�����ܻ�Ӱ���ں�̨���е��������̡�������ʹ��-l���������ڸ��ƹ�����ʹ�õĴ����������������
        scp -l 100 Hello1 tuts@192.168.83.132:/home
        ʹ�����100Kb / s���ٶȽ��и��ƹ���
    8.ʹ���Զ���˿ں�:
        scp -P 22 Hello1 tuts@192.168.83.132:/home
    9.���ƺͱ����ļ�����:���Ҫ�����ļ�������Ȩ�ޣ��޸�ʱ�䣬����ʱ������ԣ�����SCP������ʹ��-p�������������������
        scp -p Hello1 tuts@192.168.83.132:/home
    10.ʹ��-q��������SCP���:�����������ӡSCP���������֪ͨ�������������ȱ�������ʹ��-q������ʵ�������ò�����ֹ��ʾ����SCP�����
        scp -q Hello1 tuts@192.168.83.132��/ home / tuts / FOSSLINUX
    11.ʹ��SCP���ļ���Զ���������Ƶ����ؼ������
        scp tuts@192.168.83.132:/home/tuts/FOSSLINUX/serverFile.txt /home/tuts/FOSSLINUX
    12.�����ļ���Ŀ¼����ʹ������
        ͨ�������������֤������ʹ�õ�SSH��Կ�������������벽��    
        ssh-keygen -t rsa               ��ϵͳӦ����һ��SSH��Կ��
        ssh-copy-id root@192.168.4.200  ������Կ���Ƶ����ǵ�Զ�����������������֤��
        scp Hello1 tuts@192.168.83.132:/home ����ֱ�Ӹ��ƣ�����Ҫ���롿
    13.SCPʹ��AES����/��������ȫ�ظ����ļ������ǣ�����ʹ��-c����ָ���������뷽����ע�⣬c��Сд��ĸ����ѹ����ͬ������c�Ǵ�д��ĸ���������������
        scp -c aes128-gcm@openssh.com TESTFILE tuts@192.168.83.132:/home    ��AES���ܡ�
        scp -c blowfish TESTFILE tuts@192.168.83.132:/home                  �������㡿
    14.ʹ��SSH��Կ�ļ��������룺SCP������ʹ��-i��������Կ�ļ���ʹ����Կ�ļ���������������������֤���̡��������������
        scp -c privateKey.pem TESTFILE tuts@192.168.83.132:/home
    15.ʹ��SCP Shell�ű������ļ�:���������붨��ʹ��SCP�������Ա�дһ��Shell�ű������������̡��ڱ����У����ǽ���дһ���ű����ýű���destfile.txt�ж�ȡĿ��������
        destfile.txt�ļ�����
            192.168.83.132  
        �ű��ļ���scp.sh
            echo "STARTING SCP SCRIPT"
            echo
            echo -e "Enter the path to the file you wish to copy:\c"
            read file
            for dest in `cat /tmp/destfile.txt`; do
            scp -rC $file ${dest}:/tmp/
            done          
        chmod 777 scp.sh
        ./scp.sh


    
        
       

        
        

    
        

 


            


        
      
        
        
              
    
    




    
