
## 1.����Ŀ�����ļ��и�Ŀ¼ʹ��maven������ʱ��

    <!-- ��ִ�е�Ԫ���ԣ�Ҳ����������� -->
    mvn install -Dmaven.test.skip=true
    ��
    <!-- ��ִ�е�Ԫ���ԣ������������࣬����target/test-classesĿ¼��������Ӧ��class -->
    mvn install -DskipTests=true
## 2.springboot��Ŀ�У���pom.xml�ļ���������������ã�
 
    <!-- ��ִ�е�Ԫ���ԣ������������࣬����target/test-classesĿ¼��������Ӧ��class -->
    <skipTests>true</skipTests> 	
    ��
    <!-- ��ִ�е�Ԫ���ԣ�Ҳ����������� -->
    <maven.test.skip>true</maven.test.skip>
    
## 3.maven��Ŀ��pom.xml�ļ���������������ã�

    <!-- ��ִ�е�Ԫ���ԣ������������ಢ��target/test-classesĿ¼��������Ӧ��class -->
    <plugin>  
        <groupId>org.apache.maven.plugins</groupId>  
        <artifactId>maven-surefire-plugin</artifactId>  
        <version>2.5</version>  
        <configuration>  
            <skipTests>true</skipTests>  
        </configuration>  
    </plugin>
