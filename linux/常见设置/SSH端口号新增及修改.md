

#linux������ͨ��SSH�˿ں����Ӻ��޸ģ�
    
    ���鿴��ǰlinux�Ƿ��Ѿ���װSSH����� rpm -qa|grep ssh
    ���޸Ķ˿ںţ�vi /etc/ssh/sshd_config 
        ����궨λ��port  22���и���һ��insert����༭22�˿�Ϊ21578
    ��:wq---�����˳�
    ������ssh����/etc/init.d/sshd restart
