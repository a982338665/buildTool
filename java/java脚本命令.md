

###1.�������

    1.Windows+R��
        ��/c close   �ر�
        ��/k keep    ����
        cmd /c echo name    �ڵ�ǰcmd�����£�ִ��echo name����ɺ�رմ��ڣ����Դ�������һ�¼��ر�
        cmd /k echo name    �ڵ�ǰcmd�����£�ִ��echo name����ɺ󱣳ִ��ڣ�����ִ����������������Դ�ӡ�������Ҵ��ڱ���
            name
            C:\Users\Administrator>
        cmd /c start echo name    --һ��dos
            �򿪵�ǰcmd��ִ������start echo name,ִ����󣬵�ǰcmd�ر�
            start echo name������µ�cmd��ִ������echo name,�˴��ڻᱻ���������رյ�һ������
        cmd /k start echo name    --����dos
            �򿪵�ǰcmd��ִ������start echo name,ִ����󣬵�ǰcmd����
            start echo name������µ�cmd��ִ������echo name,�˴����Իᱻ����
        taskkill /f /im cmd.exe
            ǿ��ɱ�����е�cmd����
        cmd  /c start mvn spring-boot:run
            �¿�һ������ִ������mvn spring-boot:run
    2.java����
        //�ر�����cmd
        Process exec = Runtime.getRuntime().exec("taskkill /f /im cmd.exe");
        while (exec.isAlive()){
            Thread.sleep(1000);
            System.err.println("�ȴ�cmd�ر�...");
        }
        //���´��ڣ��ڵ�ǰ�ļ����£�ִ������mvn
        Runtime.getRuntime().exec("cmd  /c start mvn spring-boot:run", null, new File("./"));
