

**1.������ԣ�**

    --��Ŀ���ʱ���Զ�������������������֪���Խ������ֻ����� mvn install ����ִ�У����ȫ�����в���
    --������Ԫ���Խ��д�����
            mvn clean package -Dmaven.test.skip=true
            mvn install -DskipTests

**2.mvn������**

    1.maven������
        mvn spring-boot:run
    2.java������ָ���ⲿ�����ļ�
        java -jar -Dspring.config.location=application.yml  xxxx.war
        ���ͣ�
            ���������application.yml �����xxx.war ͬ��Ŀ¼��, �����Լ�ָ��, �����Ϳ���ʹ������������ļ����ǵ�war������������ļ���
    3.maven������ָ���ڲ������ļ�
        application.properties�����У�spring.profiles.active=dev
        application-dev.properties �����У�server.port=8081
        application-prod.properties �����У�server.port=8082
        ���
        [Maven����prod����ָ��Profileͨ��-P]: -- �����񲻿����á�
            `mvn spring-boot:run -Pprod`��������Maven��Profile��
        [ָ��spring-boot��spring.profiles.active�������ʹ��]��
            `mvn spring-boot:run -Drun.profiles=test`����test����   
    4.java������ָ���ڲ������ļ�
        `java -jar -Dspring.profiles.active=test demo-0.0.1-SNAPSHOT.jar`����test����
        java -jar girl-0.0.1-SNAPSHOT.jar --spring.profiles.active=deve
    5.����������������������
        `--spring.profiles.active=test`����test����
    
        
**3.ָ���˿ڣ�**
    
    mvn spring-boot:run -Dspring-boot.run.arguments=--server.port=8999
