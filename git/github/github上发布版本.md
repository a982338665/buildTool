
#��Դ��https://help.github.com/cn/packages/using-github-packages-with-your-projects-ecosystem/configuring-apache-maven-for-use-with-github-packages
#github�����ĵ���https://help.github.com/cn/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line

###1.github���ĵ�������
    
    1.ʹ��github�����洢��ִ�а�
    2.���
        ��github��ע���������йܷ�������˽�»򹫿��й����������������������Ŀ�е������maven������
        ������������jar������Ŷgithub��ע���������ʹ������
        ����װ������github��ע���װ�����������������Լ���Ŀ�е�������

###2.�����͹����

#####2.1github��ע���
    
    1.GitHub ��ע��� ������ GitHub Free��GitHub Pro����֯�� GitHub Free��GitHub Team��GitHub Enterprise Cloud �� GitHub One
    2.������һ���ֿ����йܶ��������ͨ���鿴���������ļ�������ͳ�ơ��汾��ʷ�ȣ��˽�ÿ�����ĸ�����Ϣ��
    3.���Խ� GitHub ��ע��� �� GitHub API��GitHub ���� �Լ� web �ҹ�������һ���Դ����˵��˵� DevOps �������̣����а������Ĵ��롢CI �Ͳ���������  
    4.������ѣ�˽���շ�
    5.֧�ֵĿͻ��˺͸�ʽ��
    
 ���ͻ���	|����	|����ʽ	|����
 |----|----|---|---|
|npm 	|JavaScript     |package.json   |�ڵ��������
|gem 	|Ruby	        |Gemfile	    |RubyGems��������
|mvn	|Java	        |pom.xml	    |Apache Maven ��Ŀ�������⹤��
|gradle	|Java	        |build.gradle �� build.gradle.kts	|Java �� Gradle �����Զ�������
|docker	|������	        |Dockerfile	    |Docker ��������ƽ̨
|dotnet CLI	|.NET	    |nupkg	        |.NET �� NuGet ������

    6.���ƣ������Ʋſ��Խ��а�����
        1.���˷�������ֱ���� GitHub ��ע��� �� GitHub API ��֤�����û���
        2.����ʹ�� GITHUB_TOKEN ��ͨ�� GitHub ���� �������̽��������֤
        3.����Ȩ�޷��䣺
            ���ذ�װ�������Ʊ������ read:packages �����򣬲��������û��ʻ�����Ըòֿ���ж�ȡȨ�ޡ� �����˽�вֿ⣬�������ƻ�������� repo ������
            GitHub ��ɾ��˽�а����ض��汾���������Ʊ������ delete:packages �� repo ������ �������޷�ɾ��
        4.Ȩ��������
 ������	        |Description	                    |�ֿ�Ȩ��
|----|----|----|
|read:packages	|�� GitHub ��ע��� ���غͰ�װ��	|��ȡ
|write:packages	|�����ϴ��ͷ����� GitHub ��ע���	|д��
|delete:packages|�� GitHub ��ע��� ɾ��˽�а����ض��汾	|����Ա
|repo	        |��װ���ϴ���ɾ��˽�вֿ��е�ĳЩ������Ӧ read:packages��write:packages �� delete:packages��	|��ȡ��д������Ա            
        5.���� GitHub ���� ��������ʱ��������ʹ�� GITHUB_TOKEN �����Ͱ�װ GitHub ��ע��� �еİ�������洢�͹�����˷�������
        6.�������л� API ��ͨ�� HTTPS ִ�� Git ����ʱʹ������������
        7.��Ϊ��ȫԤ����ʩ��GitHub ���Զ�ɾ��һ����δʹ�ù��ĸ��˷������ơ�
    7.���ƴ�����https://help.github.com/cn/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line
    8.���Ʊ��ܣ� ��Դ�����һ���Դ��������ƣ�ȷ��������ԡ� ʹ�� API ʱ��Ӧ�������������������������ǽ���Ӳ���뵽�����С�
    9.����ʹ�ã������������������������ƣ�
        $ git clone https://github.com/username/repo.git
        Username: your_username
        Password: your_token
        ע�⣺���˷�������ֻ������ HTTPS Git ������ ������Ĳֿ�ʹ�� SSH Զ�� URL������Ҫ��Զ�� URL �� SSH �л��� HTTPS
    10.��������ƹ��ں��滻��https://help.github.com/cn/github/using-git/updating-credentials-from-the-osx-keychain
    
**3.������**

    �ҵ���Ҫ��������Ŀ���ڸ�Ŀ¼�´������
    mvn install
    mvn deploy -Dregistry=https://maven.pkg.github.com/a982338665 -Dtoken=XXXXX
    �޸ı��زֿ� .m2Ŀ¼�µ�settings.xml,ָ��˽����˺�����
            <?xml version="1.0" encoding="UTF-8"?>
            <settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
                      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                      xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
                <servers>
                  <server>
                     <id>github</id>
                     <username>a982338665</username>
                     <password>XXX</password>
                  </server>
                </servers>
            </settings>
    �������Ŀ��pom����ӣ�
        <distributionManagement>
                <repository>
                    <id>github</id>
        <!--            <name>pers.lish</name>-->
                    <url>https://maven.pkg.github.com/a982338665/customRPC</url>
                </repository>
            </distributionManagement>

        
        
        
