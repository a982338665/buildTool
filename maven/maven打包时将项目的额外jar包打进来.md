
## ǰ��
>http://element-ui.cn/news/show-17222.aspx
>ǰ��
> ����Ŀ�����У���Ŀ��maven������һ��maven��Ŀ��
> һ�������jar��������ʹ��pom.xml�����ù�����Ҳ��һЩʱ��������Ŀ��ʹ����һ���ڲ�jar�ļ�����������ļ�������û�п��ŵ�maven���С�
> ���ǻὫ�ļ��ŵ�������ĿWEB-INF/lib�С������springboot��Ŀ�ŵ�resources/lib��
> ������ǲ���pom.xml�����������õĻ���maven����ǲ����Զ�ȥ���úͱ���lib�е�jar�ļ��ģ�������Ҫ�����޸���pom.xml�ļ������µ����Ҳ���������


## 1.����һ��Maven�ṩ��scopeΪsystem�����������ǿ�����maven�н�����������
     
      <dependency>
          <groupId>com.jd.cps</groupId>
          <artifactId>jd-cps-client</artifactId>
          <version>2.2</version>
          <scope>system</scope>
          <systemPath>${project.basedir}/src/main/resources/lib/jd-cps-client-2.2.jar</systemPath>
      </dependency>

      ���ַ�ʽ��jar�ĸ�������ʱ�ǳ����㣬����һ��jar��ʱ�ͻ��Եú��鷳�ˡ�����������ܷ�����������libĿ¼���ø�Ŀ¼������jar����������룬����������Խ����������
      
## 2.��pom�ļ�������maven-compiler-plugin�����ñ������<compilerArguments>�����extdirs��jar�����·����ӵ������У����£�
    
    <pluginManagement>
       <plugins>
           <plugin>
               <groupId>org.apache.maven.plugins</groupId>
               <artifactId>maven-compiler-plugin</artifactId>
               <version>3.1</version>
               <configuration>
                   <source>1.8</source>
                   <target>1.8</target>
                   <encoding>UTF-8</encoding>
                   <compilerArguments>
                       <extdirs>${project.basedir}/src/main/resources/lib</extdirs>
                   </compilerArguments>
               </configuration>
           </plugin>
       </plugins>
    </pluginManagement>

    ��Ҫע��һ�£���maven3.1�汾�Ժ�maven-compiler-plugin��compilerArguments��Ϊ��ʱ�ˣ����ʹ�õ�maven�汾����3.1�����������ѱ���������Ҫ�������޸ģ�
    
    <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.1</version>
        <configuration>
            <source>1.8</source>
            <target>1.8</target>
            <encoding>UTF-8</encoding>
            <compilerArgs> 
                <arg>-verbose</arg>
                <arg>-Xlint:unchecked</arg>
                <arg>-Xlint:deprecation</arg>
                <arg>-extdirs</arg> 
                <arg>${project.basedir}/src/main/resources/lib</arg>
            </compilerArgs> 
        </configuration>
    </plugin>
    
    ����������Ƿ���pom�ļ��е�buildԪ���ڡ�${project.basedir}��pom�ļ����������ԣ�ָ������Ŀ�ĵĸ�¼��
    ����${project.basedir}һ��Ҫд����Ȼ����֡���windows���¿����������룬��Linux�������Ͼ͡��п��ܡ����ֱ����Ҳ���jar���Ĵ���
