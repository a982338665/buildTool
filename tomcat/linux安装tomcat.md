
**4.tomcat��װ���ã�**   
    
    1.��ַ��https://tomcat.apache.org/download-90.cgi
    2.���ӵ�ַ��http://mirrors.shu.edu.cn/apache/tomcat/tomcat-9/v9.0.10/bin/apache-tomcat-9.0.10.zip
    
    3.��װ��
        wget ...    ����
        unzip ...   ��ѹ��
    4.����Ɉ��Й���
        cd apache-tomcat-9.0.10
        chmod a+x -R *   --�otomcat�������ļ������ִ��Ȩ��
            a+x������linux��¼��������
            -R��ǰ·���¼�������·��
            *����·���������ļ���
    5.�˿��޸ģ�
        vim conf/server.xml
    6.���в��ԣ�
        bin/startup.sh
        ps -ef |grep tomcat
    7.��������ԣ�
        ip+8080  
        �����windows���޷�����VM�е�linux�е�tomcat���볢�Թرշ���ǽ
