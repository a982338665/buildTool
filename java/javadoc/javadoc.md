#Maven��Java8����κ���Javadoc�ı���������

    JavaDoc���And����֪ʶ
    (һ) Javaע������
    //���ڵ���ע�͡�
        /*...*/���ڶ���ע�ͣ���/*��ʼ����*/����������Ƕ�ס�
        /**...*/����Ϊ֧��jdk����javadoc.exe�����е�ע����䡣
        ˵����javadoc �����ܴ�javaԴ�ļ��ж�ȡ������ע�ͣ�����ʶ��ע������@��ʶ��һЩ���������������������Html��ʽ����˵���ĵ���javadoc�����ܶ�һ�� javaԴ�ļ�����ע���ĵ��������ܶ�Ŀ¼�Ͱ����ɽ������ӵ�html��ʽ����˵���ĵ���ʮ�ַ��㡣
    (��)JavaDoc�г��ֵ�@�ַ��������壺
    1. ͨ��ע��
    ע���п��Գ��ֵĹؼ�����@��ʼ
    ����
    @author
    ������
    @version
    �汾��ʶ
    @since
    ������ֵ�JDK�汾
    @deprecated
    �����Ƽ�ʹ�õľ���  
    @see
    ����ο�
    2. ����ע��
    @return
    ����ֵ
    @throws
    �쳣�༰�׳�����
    @param
    ��������������
    ����
    
    ���ˣ�������һЩ������֪ʶ�����濪ʼ���ĵ����ġ�
    Java8��JavaDoc���﷨���ǳ��ϸ����ڽ���Maven���뷢����Ŀ��Maven Center�Ĺ����У�����������ΪJavaDoc����ʧ����ɷ���ʧ�ܣ����Ǻܶ�����£�����һ����@param����û��дȫ��@returnû��д֮������⣬Ϊ�ˣ��Ҿ��÷ǳ��б�Ҫ������Щ�쳣��
    ��������
    ��λӦ�ö�֪������һ��Maven��Ŀ��Maven������ֿ��Ǳ���Ҫ��JavaDoc����������ʹ��Maven JavaDoc plugin�Ĺ����У�һ������ĳЩ�����ڴ˵����⣺
    Failed to execute goal org.apache.maven.plugins:maven-javadoc-plugin:2.7:jar (attach-javadocs) on project [projectname]: MavenReportException: Error while creating archive:
    Exit code: 1 - [path-to-file]:[linenumber]: warning: no description for @param
    �������������������ʧ�ܣ�����취һ����һ��һ���İ���Щ@param����ȥ��һ�������ã����������Ŀ�г�ǧ������أ�
    
    ����취
    ֱ���޸�Maven JavaDoc plugin�����ã�������Щ����
    
    <plugin>
     <groupId>org.apache.maven.plugins</groupId>
     <artifactId>maven-javadoc-plugin</artifactId>
     <version>2.10.3</version>
     <executions>
     <execution>
     <id>attach-javadocs</id>
     <goals>
     <goal>jar</goal>
     </goals>
     <configuration> 
     <additionalparam>-Xdoclint:none</additionalparam>
     </configuration>
     </execution>
     </executions>
    </plugin>
    �������ԣ����Ժ���Ŀ��������������������ʲôӰ�졣
