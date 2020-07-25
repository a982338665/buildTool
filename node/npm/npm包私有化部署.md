
#https://www.jianshu.com/p/a9540d9f8d9c

## Nexus˽����
>Nexus ���Ӧ��֪���Ƕ� Maven �������˽�����ߣ���ʵ����֧�� npm ��docker ��yum �ȵ�  
>�Ƽ��鿴�ٷ�ʹ�÷�ʽ��https://blog.sonatype.com/using-nexus-3-as-your-repository-part-2-npm-packages
### 1.��װ����

    docker run -d --restart=unless-stopped  --name nexus \
    -p 8081:8081 -p 5000:5000 -p 5001:5001 -p 5002:5002 -p 5003:5003 -p 5004:5004 \
    --ulimit nofile=90000:90000 \
    -v /usr/local/nexus-data \
    -e INSTALL4J_ADD_VM_PARAMS="-Xms2g -Xmx2g" \
    sonatype/nexus3:3.8.0

    ������������ʣ�http://127.0.0.1:8081/
    Ĭ��ʹ�õ��û��������ǣ� admin/admin123
    
### 2.���йֿܲ⣬�û���Ϣ
    
    �Ա�����https://registry.npm.taobao.org
    Դ����https://registry.npmjs.org
    
### 3.�������
    0.�淶��
        1.package.json�Ĺ淶��https://docs.npmjs.com/creating-a-package-json-file
        2. .npmrc�ļ�����λ�ã�C:\Users\Administrator\.npmrc
    1.linux��ִ�������ȡbase64������ ��
        echo -n 'myuser:mypassword' | openssl base64
    2.�������һ��ֻ���Nexus �������������Ŀ����ʹ������.npmrc��������Ŀ�ĸ�Ŀ¼�´���һ���ļ���
      Ҳ����˵ֻҪ������ļ����Ϳ���ʹ��˽�вֿ�
      registry=http://your-host:8081/repository/npm-group/
      _auth=YWRtaW46YWRtaW4xMjM=
    3.�������Ҫ������Nexus����Ŀ���뽫�����package.json���ҵ�.npmrc�ļ��޸�Ϊ��������
        �����޸�privateΪfalse
      {
        ...
        "private": false,
        "publishConfig": {
          "registry": "http://your-host:8081/repository/npm-private/"
        }
      }
    4.������
        npm install
        npm publish
    5.���к�ʹ�ã�
        1.�ϴ�ʱ�ϴ���˽�вֿ⣬����ʱȥ��ϲֿ����أ��ȿ�����������ֿ�ģ��ֿ�������˽�вֿ�ģ�
            ʹ��ʱ������� checking installable status��ʵ����ȥgroup����Ƿ��а����������⣬���ǻ���
            npm --registry http://118.25.13.144:8081/repository/npm-group/ install report-api
        2.�����ɵ���һ������ʱ�����õ���ǰ��Ŀ
            npm install report-api
        3.��������һ������ʱ��
            1.ȫ�ְ�װ��ʹ��package.json�е� bin�µ������ֱ��ִ��
                npm i -g report-api
                ж��ȫ��
                npm uninstall -g report-api
                ʾ����
                    C:\Users\Administrator\xxx>npm i -g node-static-web
                    C:\Users\Administrator\xxx>node-static-web ��ֱ�����������ȡ��package.json�е�bin�µ����ݡ�
            2.�ֲ���װ��ʾ��
                C:\Users\Administrator\xxx>npm i  node-static-web
                C:\Users\Administrator\xxx>cd node_modules/.bin/
                C:\Users\Administrator\xxx\node_modules\.bin> node-static-web��ֱ�����������ȡ��package.json�е�bin�µ����ݡ�
    6.ɾ����
        npm unpublish --force //ǿ��ɾ��
        npm unpublish guitest@1.0.1 //ָ���汾��
        npm deprecate //ĳЩ���
        
    7.npm install report-api ʱ
        ����npm��ʷ���棺sudo npm cache clean
        ����npm�ֿ�ԴΪ�Ա�Դ��npm config set registry https://registry.npm.taobao.org
        ��֤һ�½�������ݣ��ⲽ���Բ���������npm config get registry ��  npm info express
    
    8.ע�⣬ʹ�ã�
    
    
    
    

