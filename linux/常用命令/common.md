**1.�������**

     1.linux�ں˳��ã�ubuntu��centos
            --1.www.ubuntu.com/download/server  -->��ʹ�ò�������汾�ģ�������������ʹ����LTS��β��
     2.linuxϵͳ�����ٶȿ죬�������ڷ�����
     3.linux���
         --1.�ػ����
             1��halt   ���̹ػ� 
             2��poweroff  ���̹ػ� 
             3��shutdown -h now ���̹ػ�(root�û�ʹ��) 
             4��shutdown -h 10 10���Ӻ��Զ��ػ� 
         --2.�������
             1��reboot 
             2��shutdown -r now ��������(root�û�ʹ��) 
             3��shutdown -r 10 ��10�����Զ�����(root�û�ʹ��)  
             4��shutdown -r 20:35 ��ʱ��Ϊ20:35ʱ������(root�û�ʹ��) 
                �����ͨ��shutdown�������������Ļ���������shutdown -c����ȡ������
         --3.�鿴Ŀ¼�ļ����
             1.ls
             2.ll
             3.ls -a --��ʾ�����ļ�
         --4.����Ŀ¼��
             1.mkdir 
             2.mkdir -p �ݹ鴴��Ŀ¼
         --5.�����ļ�;
             1.touch a.txt
         --6.����ӡ����д���ļ�
             1.echo "hello" > test.txt
             2.echo "hello" >> test.txt      --��ԭ�ļ���׷���ı�hello���ỻ�У�
         --7.�鿴�ļ���
             1.cat test.txt  --ȫ��
             2.more test.txt --��ҳ��ʾ�ļ�
             3.head test,txt --��ʾ�ļ���ͷ
             4.tail test.txt --��ʾ�ļ���β
             5.tail -f       --��ʾʵʱ��־
             6.stat test.txt --��ʾ�ļ���ϸ��Ϣ����С�����͵�
         --8.���ƣ��ƶ�(Ҳ��������)��ɾ��
             1.cp
             2.mv
             3.rm 
         --9.�����ļ���
             1.find -m "*test"   --�鿴��ǰ�ļ�������test��β���ļ�
         --10.����ĳ�ļ���ĳ���ݣ�
             1.cat test.txt | grep linux     --��test.txt�ļ��в��Һ�linux���ַ���
         --11.��ʾ��ǰ·��
             1.pwd
         --12.��ʾ�������ƣ�
             1.hostname
         --13.��ʾ��ǰ��¼�û�
             1.who
         --14.��ʾϵͳ��Ϣ
             1.uname
         --15.��ʾ��ǰϵͳ�кķ���Դ���Ľ���--��ͬ��windows�����������
             1.top
         --16.��ʾ˲�����״̬��
             1.ps  
         --17.��ʾָ���ļ�������Ŀ¼�Ѿ�ʹ�õĴ��̿ռ������
             1.du -h
         --18.��ʾ�ļ�ϵͳ���̵Ŀռ�ʹ�����
             1.df -h
         --19.��ʾ��ǰ�ڴ�ͽ����ռ��ʹ�������
             1.free -h
         --20.��ʾ����ӿ���Ϣ;
             1.ifconfig
         --21.��ʾ����״̬��Ϣ
             1.netstat
         --22.�������糩ͨ��
             1.ping ��ַ
         --23.����
             1.clear
         --24.ɱ�����̣�
             1.kill  -9 pid
         --25.�ļ���ѹ��:
             1.tar -zcvf yasuo.tar.gz download/  ��download�ļ���ѹ��Ϊyasuo.tar.gz��
         --26.�ļ���ѹ��
             1..tar -zxvf yasuo.tar.gz
         --27.�ļ��༭��vim file
             1.:q            ֱ���˳�
             2.:q!           ǿ���˳�
             3.:wq           ������˳�
             4.:set number   �ڱ༭�ļ���ʾ�к�
             5.:set nonumber �ڱ༭�ļ�����ʾ�к�
             6.:w file       ����ǰ���ݱ����ĳ���ļ�
         --28.�޸�����Դ��--
         --29.��װ�����
             1.yum install tree -y   --��װ��-y��ʾyes
             2.tree                  --��ʾ��ǰ�ṹĿ¼��
         --30.�����ӣ������ڿ�ݷ�ʽ
             1.ln /test/t.txt mm.txt --��ǰĿ¼��mm.txt�ļ���/test/t.txt�ļ��������ӣ��޸����������ݣ�ԭt.txt�ļ�Ҳ�ᱻ�޸�
         --31.ж�������
             1.yum erase nginx -y 
         --32.linux�û����û������linux֧�ֶ��û���¼ʹ����Դ
             1.passwd root           --��root�û������������������
             2.exit(����ctrl+d)      --�Ƴ�root�û���¼
             3.cat /etc/passwd       --�鿴ϵͳ�û���Ϣ��ÿ�д���һ���˺�
             4.userdel -r �û���      --ɾ���û�
             5.id �û���              --�鿴�û���Ϣ
         --33.����Ȩ�޲�����
             1.rwx���ֱ�������д����ִ��Ȩ��
             2.���ԣ�
                 vi test.sh ���
                     #!/bin/bash        --ѡ��ִ����
                     echo "hello"    --��ӡhello
                 :wq
                 chmod +x test.sh    --�����ļ����xȨ��--��ִ��
                 ./test.sh           --ִ���ļ�
             3.chown -R root:root jdk1.8/    --��jdk1.8����ļ��е��û�������Ϊroot�û����µ�root�û�
             
**2.vm��centos��windows�������⣺**
    
    ����linux�����û������룺
    linux��=
    	--admin	
    	--root
    ------------------------------------------------------
    linux����겻�ɼ���
    	--���µ�½
    ------------------------------------------------------
    linux�����л�dos�նˣ�
    	--Ctrl+alt+F2 ����F3-5
    	--�л������棺Ctrl+alt+F1
    linuxͼ�������dos����
    	--Applications--SystemTools--Terminal
    ------------------------------------------------------
    linux��dos�ն��л������棺
    	--Ctrl+alt+F1
    linux��dos�����е�¼������˳���
    	--exit
    window10ϵͳ�����������������linuxϵͳ��������л�ʱ��
    	--Ctrl+alt

**3.linux���þ�̬ip��ַ��**

    ���Թ���Ա�������
    	su root
    ���鿴ip��ַ��
    	ifconfig -a  ���� ip add
    	��סip��102.168.6.128/24
    �����þ�̬��ַ��
    	vi /etc/sysconfig/network-scripts/ifcfg-eth0
    	������
    	IPADDRO=192.168.6.128
    	GATEWAYO=192.168.6.1
    	DNS1=192.168.6.1
    	PREFIXO=24
    	�޸ģ�
    	#BOOTPROTO=dhcp(dhcpΪ�Զ�����ip��ַ,���ǰ���ע���ˣ������������)
    	BOOTPROTO=static(�����)
    ������������ service network restart
    �������˳���
    	:wq
    	:q!---ǿ���˳�������
    ��������shutdown -r now
    
**��Ҫ��**

    1. �鿴tomcat����
        ps -aux | grep tomcat
        ������ps -ef | grep tomcat���У�
        [plain] view plain copy
            root      1537  0.1  3.7 12829256 1248140 ?    Sl   Oct13   <span style="font-family: Arial, Helvetica, sans-serif;">...��������������ʡ�ԣ�</span>  
            tomcat7  14177  1.3  0.3 3202376 124332 ?      Sl   10:02   <span style="font-family: Arial, Helvetica, sans-serif;">...��������������ʡ�ԣ�</span>  
        ���Կ�����������������tomcat���̣�һ�����̵�pidΪ1537����һ��pidΪ14177��
    2. ���ݽ��̲鿴�˿ں�
        sudo netstat -naop | grep 14177
        ���Կ���8055��8088�˿ںű�ռ�ã�����805��tomact Server��SHUTDOWN�Ķ˿ںţ�8088��tomcat��CATALINA Service��Connector�Ķ˿ںš�
    3. ���ݶ˿ںŲ鿴����
        sudo lsof -i:8088
        [plain] view plain copy


**3.������**

    ��������������������������������������������������������������������������������
    �����ļ��У�
    	find / -name pub ����������ǰ�ļ����µ�ָ����pub�ļ���
    	
    �鿴linuxϵͳ�µ������û���
    	grep bash /etc/passwd �Ϳ��Եõ����е���ͨ�û�
    �鿴ϵͳ�����û���Ϣ��
    	cat /etc/passwd
    ɾ��linux�û���Ϣ��
    	userdel  xiaoluo  
    	������ɾ�����û��˺����������Ϣ���ٴδ������û�ʱ���ᱨ��
    	��ֻ��ɾ������/etc/passwd��/etc/shadow��/etc/group/��/etc/gshadow�ĸ��ļ���ĸ��˻��������Ϣ
    ��ȫɾ���˺ţ�
    	1.userdel -r xiaoluo
    	2.userdel xiaoluo 
    	  find / -name "*xiaoluo*"
              ʹ��rm -rf ɾ��
    �鿴�û��飺
    	1.groups yonguhming
    �鿴/etc/group �ļ�
    	1.cat /etc/group | sort			��ѯ�������	
    	2.cat /etc/group | grep -E "shiyanlou"  ��ѯ�������
    	root1:x:5000:
    	�������ݷֱ��ʾ�û��飬����(x��ʾ���벻�ɼ�)��GID�����û���������û�
    ��������linux��
    	shutdown -r now �������� 
    	reboot		��������
    	shutdown -h now �����ػ�
    	shutdown -h 5 	5���Ӻ�ػ�
    	shutdown -r 5 	5���Ӻ�����
    
    		            
