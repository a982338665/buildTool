

start /min node ./bin/www   [��̨����Ӧ�ó���] ==�����ǻ��д��ڴ���


netstat -aon |findstr 3011  �鿴���̺�
tasklist |findstr 468 �鿴������
taskkill /f /t /im ���̺�




## 2.forever����

    npm i -g forever
    
    ����forever���Կ�����һ��nodejs���ػ����̣��ܹ�������ֹͣ���������ǵ�appӦ�á�
    
    1.ȫ�ְ�װ forever
    // �ǵü�-g��foreverҪ��װ��ȫ�ֻ����� 
    sudo npm install forever -g
    2.����
    ���ƴ���
    // 1. �򵥵����� 
    forever start app.js 
    
    // 2. ָ��forever��Ϣ����ļ�����Ȼ��Ĭ������ŵ�~/.forever/forever.log 
    forever start -l forever.log app.js 
    
    // 3. ָ��app.js�е���־��Ϣ�ʹ�����־����ļ��� 
    // -o ����console.log�������Ϣ��-e ����console.error�������Ϣ 
    forever start -o out.log -e err.log app.js 
    
    // 4. ׷����־��foreverĬ���ǲ��ܸ����ϴε�������־�� 
    // ��������ڶ�����������-a����᲻������ 
    forever start -l forever.log -a app.js 
    
    // 5. ������ǰ�ļ����µ������ļ��Ķ� 
    forever start -w app.js 
    ���ƴ���
    3.�ļ��Ķ��������Զ�����
    // 1. ������ǰ�ļ����µ������ļ��Ķ�����̫���������� 
    forever start -w app.js 
    4. ��ʾ�������еķ���
    forever list 
    5. ֹͣ����
    ���ƴ���
    // 1. ֹͣ�������е�node App 
    forever stopall 
    
    // 2. ֹͣ����һ��node App 
    forever stop app.js 
    // ��Ȼ���������� 
    // forever list �ҵ���Ӧ��id��Ȼ�� 
    forever stop [id] 
    ���ƴ���
    6.��������
    ����������ֹͣ��������һ�¡�
    // 1. �������� 
    forever restartall
