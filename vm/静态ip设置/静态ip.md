
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
    

