



#���������������⣺

    $ service sshd status 
      openssh-daemon is stopped
    �����
    ----
    �Բ�������ʱ��
    ��rpm -qa| grep iptables #�鿴�Ƿ�װ��iptables����ǽ
    �������װ�ˣ��༭����ǽ�����ļ�
    	vi /etc/sysconfig/iptables
     	#���ӵĹ���(�˿ںŸ�Ϊ�Լ��ģ���ֹ22�˿ڵ�½Ҳ���������ｫ22�˿ڵĹ���ɾ��
     	-A RH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport 21578 -j 	ACCEPT
    	-A INPUT -m state --state NEW -m tcp -p tcp --dport 80 -j ACCEPT
    ��service iptables restart  #��������ǽ
