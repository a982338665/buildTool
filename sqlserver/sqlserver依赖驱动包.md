

�ٶ����̣�20190811-soft/maven˽������

      <dependency>
            <groupId>com.microsoft.sqlserver</groupId>
            <artifactId>sqljdbc4</artifactId>
            <version>4.0</version>
        </dependency>
ע�⣺��maven˽������jar��ʧ�ܣ�Ϊ�˼��ʹ�ã�����������sqljdbc4.jar��Ȼ�����������л���jar������·����ִ��



mvn install:install-file -Dfile=sqljdbc4.jar -Dpackaging=jar -DgroupId=com.microsoft.sqlserver -DartifactId=sqljdbc4 -Dversion=4.0
