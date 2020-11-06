
## 1.��װzookeeper-3.4.6��

        ��ע�����ķ�������192.168.6.128
        1.�޸Ĳ���ϵͳ�� /etc/hosts�ļ�����ӣ�
            su root
            vi  /etc/hosts:
            #zookeeper server
            192.168.6.128 provider-01
            
            esc+:wq
        2.���أ�
            cd /home/admin/
            wget http://apache.fayea.com/zookeeper/zookeeper-3.4.10/zookeeper-3.4.10.tar.gz
        3.��ѹ��tar -zxvf zookeeper-3.4.10.tar.gz
        4.cd /home/admin/zookeeper-3.4.10
        5.����Ŀ¼
            # mkdir data 
            # mkdir logs
        6.�ļ�������
            # cd conf
            # cp zoo_sample.cfg  zoo.cfg
        7.�޸�������vim zoo.cfg
        # The number of milliseconds of each tick
        #��������������������������
        tickTime=2000 
        # The number of ticks that the initial
        # synchronization phase can take
        #��������������������������
        initLimit=10
        #����������������zookeeper���ܿͻ��˳�ʼ������ʱ������ܶ��ٸ�����ʱ������
        #�˴��Ŀͻ��ˣ����û�����zookeeper�������Ŀͻ��ˣ�����zookeeper��������Ⱥ�����ӵ�leader��follow������
        #���Ѿ�����10��������ʱ��(��tickTIme)���Ⱥ�zookeeper��������û���յ��ͻ��˵ķ�����Ϣ
        #�Ǳ�������ͻ�������ʧ�ܣ��ܵ�ʱ�䳤�Ⱦ�Ϊ5*2000=10��
        # The number of ticks that can pass between
        # sending a request and getting an acknowledgement
        #����������������������������
        #����������ʶleader��follower֮�䷢����Ϣ���������Ӧʱ�䳤�ȣ�����ܳ������ٸ�tickTime��ʱ�䳤��
        #�ܵ�ʱ�䳤�Ⱦ���2*2000=4�루֮���Գ���2����Ϊ�������Ӧ��һ�Σ�
        
        syncLimit=5
        # the directory where the snapshot is stored.
        # do not use /tmp for storage, /tmp here is just
        # example sakes.
        # ---------------------------
        dataDir=/home/admin/zookeeper-3.4.10/data
        dataLogDir=/home/admin/zookeeper-3.4.10/logs
        # ---------------------------
        # the port at which the clients will connect
        # ---------------------------
        # 2181ͨ���˶˿ڽ���ͨѶ
        clientPort=2181 
        server.1=provider-01:2888:3888
        # 2888��zookeeper����֮���ͨ�Ŷ˿�(��Ⱥʱ���õ�)��3888��zookeeper������Ӧ�ó���ͨѶ�Ķ˿�
        # ---------------------------
        # the maximum number of client connections.
        # increase this if you need to handle more clients
        #maxClientCnxns=60
        #
        # Be sure to read the maintenance section of the
        # administrator guide before turning on autopurge.
        #
        # http://zookeeper.apache.org/doc/current/zookeeperAdmin.html#sc_maintenance
        #
        # The number of snapshots to retain in dataDir
        #autopurge.snapRetainCount=3
        # Purge task interval in hours
        # Set to "0" to disable auto purge feature
        #autopurge.purgeInterval=1
        
        8.��dataDir=/home/admin/zookeeper-3.4.10/data�´���myid�ļ����༭
            # mkdir myid
            # vi myid    �������༭myid�ļ�����
            �ڶ�Ӧ��ip�Ļ����������Ӧ�ı�ţ�
            ����zookeeper�ϣ�myid�ļ����ݾ���1
            ���ڵ����Ͻ��а�װ���ã���ôֻ��һ��server.1
            �˴�����1������
        9.admin�û����޸��ļ�����zookeeper����(���û�������)
            # vi /home/admin/.bash_profile
            export ZOOKEEPER_HOME=/home/admin/zookeeper-3.4.10
            export Path=$ZOOKEEPER_HOME/bin:$PATH
            # source .bash_profile  ʹ�����ļ���Ч
        10.����ǽ��Ҫ�õ��Ķ˿ڣ�2181,2888,3888
            # su root
            # chkconfig iptables on 
            # service iptables start
            # vi /etc/sysconfig/iptables
            -A INPUT -m state --state NEW -m tcp -p tcp --dport 2181  -j 	ACCEPT
            -A INPUT -m state --state NEW -m tcp -p tcp --dport 2888  -j 	ACCEPT
            -A INPUT -m state --state NEW -m tcp -p tcp --dport 3888  -j 	ACCEPT
            # service iptables restart
            # service iptables status
        11.����������zookeeper��ʹ��admin�û�������root��
            # exit �˳�root�û�
            # pwd  �鿴��ǰ·��
            # cd /home/admin/zookeeper-3.4.10/bin
            #/
            # jps --�鿴����
                1456 QuorumPeerMain  --zookeeper����
                1475 Jps
            # zkServer.sh status  --
            # zkServer.sh stop  --ֹͣ
            # ps -ef |grep java --�鿴����
        12.����zookeeper����������
            # vi /etc/rc.local	
            su - admin -c '/home/admin/zookeeper-3.4.10/bin/zkServer.sh start'

## 2.docker��װzk��
    
    1.������
        docker run -d -p 2181:2181 --restart always --name zookeeper \
        -v $PWD/volume/data:/data \
        -v $PWD/volume/datalog:/datalog \
        zookeeper:3.4.13
        ���ͣ�
            -v ����
            $PWD ָ��ǰĿ¼
            --restart always ��ʾ�ܻ�����
    2.��Ⱥ��
        -- �����ڵ��ļ���
        mkdir cluster/node1 -p && mkdir cluster/node2 -p && mkdir cluster/node3 -p
        
        -- ����ip
        machine_ip=10.82.12.95
        
        -- ���нڵ�1
        docker run -d -p 2181:2181 -p 2887:2888 -p 3887:3888 --name zookeeper_node1 --restart always \
        -v $PWD/cluster/node1/volume/data:/data \
        -v $PWD/cluster/node1/volume/datalog:/datalog \
        -e "TZ=Asia/Shanghai" \
        -e "ZOO_MY_ID=1" \
        -e "ZOO_SERVERS=server.1=0.0.0.0:2888:3888 server.2=$machine_ip:2888:3888 server.3=$machine_ip:2889:3889" \
        zookeeper:3.4.13
        
        -- ���нڵ�2
        docker run -d -p 2182:2181 -p 2888:2888 -p 3888:3888 --name zookeeper_node2 --restart always \
        -v $PWD/cluster/node2/volume/data:/data \
        -v $PWD/cluster/node2/volume/datalog:/datalog \
        -e "TZ=Asia/Shanghai" \
        -e "ZOO_MY_ID=2" \
        -e "ZOO_SERVERS=server.1=$machine_ip:2887:3887 server.2=0.0.0.0:2888:3888 server.3=$machine_ip:2889:3889" \
        zookeeper:3.4.13
        
        -- ���нڵ�3
        docker run -d -p 2183:2181 -p 2889:2888 -p 3889:3888 --name zookeeper_node3 --restart always \
        -v $PWD/cluster/node3/volume/data:/data \
        -v $PWD/cluster/node3/volume/datalog:/datalog \
        -e "TZ=Asia/Shanghai" \
        -e "ZOO_MY_ID=3" \
        -e "ZOO_SERVERS=server.1=$machine_ip:2887:3887 server.2=$machine_ip:2888:3888 server.3=0.0.0.0:2888:3888" \
        zookeeper:3.4.13
