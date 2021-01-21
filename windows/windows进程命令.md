


## 1.windows�Դ���������ʽ

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

## 3.pm2������ʽ
    
    1��ȫ�ְ�װpm2
        npm install pm2 -g
    2��ȫ�ְ�װwindow������
        npm install pm2-windows-startup -g  
    3������pm2
        pm2-startup install
    4�������ļ�·�������Ʋ�����
        pm2 start ·�� --name ���� --watch
        pm2 start  D:\�ҵļ����\����ʵ����Ŀ\����\main.js --name  ���� --watch
    5�����浽pm2ʵ������ �����������������Ѳ��ԣ�
        pm2 save
    6���鿴���������б�,����һ�¾Ϳ���֪���ǲ��ǳɹ���
        pm2 ls

    PM2���
        PM2��node���̹�����
    ����
        �Cwarch:����Ӧ��Ŀ¼�ı仯��һ�������仯���Զ����������Ҫ��ȷ��������������Ŀ¼�����ͨ�������ļ���
        -i --instances: ���ö��ٸ�ʵ���������ڸ��ؾ��⡣���-i 0 ����-i max������ݵ�ǰ��������ȷ��ʵ����Ŀ��
        �Cignore-watch���ų�������Ŀ¼/�ļ����������ض����ļ�����Ҳ���������򡣱���Cignore-watch=��test node_modules ��some scripts����
        -n --name��Ӧ�õ����ơ��鿴Ӧ����Ϣ��ʱ������õ���
        -o --output ����׼�����־�ļ���·����
        -e --error �����������־�ļ���·����
        �Cinterpreter ��the interpreter pm2 should use for executing app (bash, python��)���������õ�coffee script����дӦ�á�
    ����
        pm2 restart app.js
    ֹͣ
        pm2 stop ���ƻ�id
    ֹͣ����
        pm2 stop all
    ɾ��
        pm2 delete app_name|app_id
        pm2 delete all
    �鿴����״̬
        pm2 list
    �鿴��־
        pm2 logs

## 4.��װ
     npm install -g pm2
     
     �÷�
     $ npm install pm2 -g     # �����а�װ pm2 
     $ pm2 start app.js -i 4 #��̨����pm2������4��app.js 
                                     # Ҳ���԰�'max' �������ݸ� start
                                     # ��ȷ�Ľ�����Ŀ������Cpu�ĺ�����Ŀ
     $ pm2 start app.js --name my-api # ��������
     $ pm2 list               # ��ʾ���н���״̬
     $ pm2 monit              # �������н���
     $ pm2 logs               #  ��ʾ���н�����־
     $ pm2 stop all           # ֹͣ���н���
     $ pm2 restart all        # �������н���
     $ pm2 reload all         # 0��ͣ�����ؽ��� (���� NETWORKED ����)
     $ pm2 stop 0             # ָֹͣ���Ľ���
     $ pm2 restart 0          # ����ָ���Ľ���
     $ pm2 startup            # ���� init �ű� ���ֽ��̻���
     $ pm2 web                # ���н�׳�� computer API endpoint (http://localhost:9615)
     $ pm2 delete 0           # ɱ��ָ���Ľ���
     $ pm2 delete all         # ɱ��ȫ������
     
     ���н��̵Ĳ�ͬ��ʽ��
     $ pm2 start app.js -i max  # ������ЧCPU��Ŀ������������Ŀ
     $ pm2 start app.js -i 3      # ����3������
     $ pm2 start app.js -x        #��forkģʽ���� app.js ������ʹ�� cluster
     $ pm2 start app.js -x -- -a 23   # ��forkģʽ���� app.js ���Ҵ��ݲ��� (-a 23)
     $ pm2 start app.js --name serverone  # ����һ�����̲���������Ϊ serverone
     $ pm2 stop serverone       # ֹͣ serverone ����
     $ pm2 start app.json        # ��������, �� app.json������ѡ��
     $ pm2 start app.js -i max -- -a 23                   #��--֮��� app.js ���ݲ���
     $ pm2 start app.js -i max -e err.log -o out.log  # ���� �� ����һ�������ļ�
     ��Ҳ����ִ�����������Ա�д��app  ( fork ģʽ):
     $ pm2 start my-bash-script.sh    -x --interpreter bash
     $ pm2 start my-python-script.py -x --interpreter python
     
     pm2 start ./bin/report.js -i max -e err.log -o out.log -x --interpreter node12 --name cdc --watch

     0��ͣ������:
     ���������������������������ʧȥ�������ӡ�
     ע�⣺
     ��������webӦ��
     ������Node 0.11.x�汾
     ������ cluster ģʽ��Ĭ��ģʽ��
     $ pm2 reload all
     
     CoffeeScript:
     $ pm2 start my_app.coffee  #�����ȫ��
     
     PM2׼����Ϊ��Ʒ����������
     ֻ������ķ������ϲ���
     $ git clone https://github.com/Unitech/pm2.git
     $ cd pm2
     $ npm install  # ���� npm install --dev �����devDependencies û�а�װ
     $ npm test
