��ѹ���unzip EtnetChinaApplication.jar -d app
ѹ�����jar cvfm0 MR-XDR-JMR-NEW.jar META-INF/MANIFEST.MF .
�ƶ����mv EtnetChinaApplication.jar ../kps.jar
��װ��� yum install zip    #��ʾ����ʱ��������y��
��װ���yum install unzip #��ʾ����ʱ��������y��
������Ŀ��nohup java -jar kps.jar --server.port=80 >> mss.log  2>& 1 &
�鿴�������еķ���ps	-a
��ѯָ�������ķ���ps -ef | grep java


docker run --detach \
            --name wx-nginx \
            -p 443:443\
            -p 80:80 \
            -v /usr/local/dockerdata/nginx/data:/usr/share/nginx/html:rw\
            -v /usr/local/dockerdata/nginx/config/nginx.conf:/etc/nginx/nginx.conf/:rw\
            -v /usr/local/dockerdata/nginx/config/conf.d/default.conf:/etc/nginx/conf.d/default.conf:rw\
            -d nginx
