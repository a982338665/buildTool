

�ٶ����̣�20190811-soft/maven˽������

      <dependency>
            <groupId>com.microsoft.sqlserver</groupId>
            <artifactId>sqljdbc4</artifactId>
            <version>4.0</version>
        </dependency>
ע�⣺��maven˽������jar��ʧ�ܣ�Ϊ�˼��ʹ�ã�����������sqljdbc4.jar��Ȼ�����������л���jar������·����ִ��



mvn install:install-file -Dfile=sqljdbc4.jar -Dpackaging=jar -DgroupId=com.microsoft.sqlserver -DartifactId=sqljdbc4 -Dversion=4.0

����jar�ϴ���˽��
    1�������Ե�¼˽��������jar
    2����Ҳ����ʹ�������ϴ�
mvn deploy:deploy-file -Dfile=jar�� -DgroupId=groupID -DartifactId=artifacid -Dversion=�汾�� -Dpackaging=jar
-Durl=http://ip:port/nexus/content/repositories/thirdparty/ -DrepositoryId=thirdparty

ʾ����
mvn deploy:deploy-file -Dfile=sqljdbc4.jar -DgroupId=com.microsoft.sqlserver -DartifactId=sqljdbc4 -Dversion=4.0 -Dpackaging=jar -Durl=http://10.116.24.33:8081/repository/common-jingniu/ -DrepositoryId=admin123

���ͣ�
mvn deploy:deploy-file 
-Dfile=sqljdbc4.jar 
-DgroupId=com.microsoft.sqlserver 
-DartifactId=sqljdbc4 
-Dversion=4.0 
-Dpackaging=jar 
-Durl=http://10.116.24.33:8081/repository/common-jingniu/ 
-DrepositoryId=admin123
