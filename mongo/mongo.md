# nosql


nosql-�ǹ�ϵ�����ݿ�



**mongodb:**

    1.key-value���ݿ⣺ʱ�临�Ӷ�O(1)
        memcached
        redis
    2.�ĵ����ݿ�(mongodb)���洢�����ĵ�-(Bson->json�Ķ����ƻ���Ķ���)
        -1.�ڲ�����ʹ��js������ʵ�ֵģ����ĵ��洢��bson�ṹ����ѯʱרת��Ϊjs���󣬲��ҿ���ͨ��js����������
    3.mongo�͹�ϵ�����ݿ�(mysql,oracle��)�Ƚϣ�
        -1.��ϵ�����ݿ�洢�ṹ�����ݣ����ñ�ṹ������һ�����ϱ�ṹ
        -2.�ĵ����ݿ⣺--�洢bson���������ݿɲ�ͬ������
            ��{id��3,name:list}
            ��{id��3,name:list,area:hubei}
            -���ĵ�Ϊ��λ���޽ṹ�����µ�ÿƪ�ĵ������Լ����صĽṹ������
        -3.��Ӱ���ظ�Ϊ����
            -��ϵ�����ݿ���ƣ�
                -��Ӱ��
                -���۱�
                -���ۻظ���
                -���۴�ּ�¼��
            -mongodb��ƣ���ͬ��������Ƽ�
                {film:'���Ĵ���',long:'120',comment[
                    {
                     content:'Ӱ��1...',
                        reply:['�ظ�1','�ظ�2']
                    },
                    {
                        ...
                    }
                ]}
            -������Ӱ�����ظ���ҵ�񳡾����ɲ����ĵ���ɣ�����ʽ��

**mongodb�İ�װ��**

    1.www.mongodb.org����
    2.https://www.mongodb.com/download-center?jmp=nav#community
    3.��linuxϵͳΪ����https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-amazon2-4.0.0.tgz
          curl -O https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-3.0.6.tgz    # ����
          tar -zxvf mongodb-linux-x86_64-3.0.6.tgz                                   # ��ѹ
          mv  mongodb-linux-x86_64-3.0.6/ /usr/local/mongodb                         # ����ѹ��������ָ��Ŀ¼
          export PATH=<mongodb-install-directory>/bin:$PATH
                #MongoDB �Ŀ�ִ���ļ�λ�� bin Ŀ¼�£����Կ��Խ�����ӵ� PATH ·���У�
                #<mongodb-install-directory> Ϊ�� MongoDB �İ�װ·�����籾�ĵ� /usr/local/mongodb
          mkdir -p /data/db
                #MongoDB�����ݴ洢Ĭ����dataĿ¼��dbĿ¼����Ҫ�ֶ�����
                #/data/db �� MongoDB Ĭ�ϵ����������ݿ�·��(--dbpath)
                #���������ݿ�Ŀ¼����/data/db������ͨ�� --dbpath ��ָ�������������ݿ�Ŀ¼����/data/db������ͨ�� --dbpath ��ָ��
          ./bin/mongod
                #����mongo����ˣ�Ĭ�϶˿� 27017
          ./bin/mongod  --rest
                #����mongo�����web�û����棺Ĭ�϶˿� 28017
                #���ʵ�ַ��http://localhost:28017
                #MongoDB �� Web ������ʶ˿ڱȷ���Ķ˿ڶ�1000
                 ������MongoDB���ж˿�ʹ��Ĭ�ϵ�27017��������ڶ˿ں�Ϊ28017����web�û�����

          ./bin/mongo
                #����mongo�ͻ������ӣ�--
                ----------------------
                --�򵥼��㣺
                > 1+1
                2
                > 1*1
                1
                ----------------------
                --���ӣ�
                > db.runoob.insert({x:10})
                WriteResult({ "nInserted" : 1 })
                --�Բ�������ݽ��м�����
                > db.runoob.find()
                { "_id" : ObjectId("5b695077c39941e6f2e7f627"), "x" : 10 }
                ----------------------
                --��ʾ�������ݿ��б�
                > show dbs
                local  0.078GB
                test   0.078GB
                --��ʾ��ǰ���ݿ����
                > db
                test
                --�л����ݿ�
                > use loacl
                switched to db loacl
                > db
                loacl
         4.��windowsΪ����
            1.����λ�ã�http://dl.mongodb.org/dl/win32/x86_64
            2.�������ļ�����ָ���ļ��У� E:\SoftMgr\MongoDB\Server\data\db
            3.�½��ļ��У�E:\SoftMgr\MongoDB\Server\data\log
            4.��cmd ���ҵ�log�ļ� ִ�� type nul>MongoDB.log
            5.ע�⣺mongod  --logpath  "E:\SoftMgr\MongoDB\Server\data\log\MongoDB.txt"
              �����־��Ҫ�ƶ�����Ȼ��־�ļ�����������.
            6.��bin��Ŀ��ִ�У�dir������������Ŀִ�У�mongod --dbpath E:\SoftMgr\MongoDB\Server\data\db
            7.��http://localhost:27017��֤

** mongo DB������� **

    1.һЩ���ݿ����Ǳ����ģ�����ֱ�ӷ�����Щ���������õ����ݿ⡣
        admin�� ��Ȩ�޵ĽǶ�����������"root"���ݿ⡣Ҫ�ǽ�һ���û���ӵ�������ݿ⣬����û��Զ��̳��������ݿ��Ȩ�ޡ�һЩ�ض��ķ�����������Ҳֻ�ܴ�������ݿ����У������г����е����ݿ���߹رշ�������
        local: ���������Զ���ᱻ���ƣ����������洢���ڱ��ص�̨�����������⼯��
        config: ��Mongo���ڷ�Ƭ����ʱ��config���ݿ����ڲ�ʹ�ã����ڱ����Ƭ�������Ϣ
    2.��ϵ�����ݿ��mongo�Ķ�Ӧ��ϵ��
        ����-������
        ���-����
        ��  -�ĵ�
        ��  -�ֶ�
        ������-Ƕ���ĵ�
        ����-������MongoDB �ṩ�� key Ϊ _id��
    3.ע�⼰�淶��
        1.�ĵ��м�ֵ���������
        2.ֵ��Ϊ�����������ͣ������ĵ�����
        3.�������ͺʹ�Сд
        4.�������ظ��ļ�
        5.�����ַ��������������������������ʹ������utf8�ַ���
        6.�������п��ַ�(��Ϊ���ַ���ʾ���Ľ�β)
        7.���»���"_"��ͷ�ļ��Ǳ�����(�����ϸ�Ҫ���)
    4.��������������
        1.����ʹ���ַ���
        2.���ܺ��п��ַ�
        3.������������"system."��ͷ������Ϊϵͳ���ϱ�����ǰ׺
        4.��Ҫ�����������$��������Ҫ��������ϵͳ�����ļ���
    5,Capped collections ���ǹ̶���С��collection��
        1.���кܸߵ������Լ����й��ڵ�����(���ڰ��ղ����˳��). �е�� "RRD" �������ơ�
        2.Capped collections�Ǹ������Զ���ά������Ĳ���˳�����ǳ��ʺ����Ƽ�¼��־�Ĺ���
        3.����Ҫ��ʽ�Ĵ���һ��capped collection�� ָ��һ��collection�Ĵ�С����λ���ֽڡ�collection�����ݴ洢�ռ�ֵ��ǰ�����
        4.ע�����ָ���Ĵ洢��С���������ݿ��ͷ��Ϣ
          db.createCollection("mycoll", {capped:true, size:100000})
        5.������
            ��capped collection�У���������µĶ���
            �ܽ��и��£�Ȼ�������󲻻����Ӵ洢�ռ䡣������ӣ����¾ͻ�ʧ�� ��
            ���ݿⲻ�������ɾ����ʹ��drop()����ɾ��collection���е��С�
            ע��: ɾ��֮���������ʽ�����´������collection��
            ��32bit�����У�capped collection���洢Ϊ1e9( 1X109)���ֽڡ�
    6.MongoDB �������ͣ�
        1.�������ĵ�����������ʱ�䣬��Ϊ�ĵ�������д���ʱ��
        2.MongoDB �д洢���ĵ�������һ�� _id �����������ֵ�������κ����͵ģ�Ĭ���Ǹ� ObjectId ����
          ���� ObjectId �б����˴�����ʱ����������㲻��ҪΪ����ĵ�����ʱ����ֶΣ������ͨ�� getTimestamp
          ��������ȡ�ĵ��Ĵ���ʱ��:
          > var newObject = ObjectId()
          > newObject.getTimestamp()
          ISODate("2017-11-25T07:21:10Z")
          ObjectId תΪ�ַ���
          > newObject.str
          5a1919e63df83ce79df8b38f
        3.���ڣ�
          ��ʾ��ǰ���� Unix�¼�Ԫ��1970��1��1�գ��ĺ������������������з��ŵ�, ������ʾ 1970 ��֮ǰ�����ڡ�
          ------------------------------------------
          > var mydate1 = new Date()     //��������ʱ��
          > mydate1
          ISODate("2018-03-04T14:58:51.233Z")
          > typeof mydate1
          object
          ------------------------------------------
          > var mydate2 = ISODate() //��������ʱ��
          > mydate2
          ISODate("2018-03-04T15:00:45.479Z")
          > typeof mydate2
          object
          ����������ʱ�����������ͣ�����ʹ�� JS �е� Date ���͵ķ�����
           ------------------------------------------
          ����һ��ʱ�����͵��ַ�����
          > var mydate1str = mydate1.toString()
          > mydate1str
          Sun Mar 04 2018 14:58:51 GMT+0000 (UTC)
          > typeof mydate1str
          string
          ����
           ------------------------------------------
          > Date()
          Sun Mar 04 2018 15:02:59 GMT+0000 (UTC)

** mongo DB-�������� **

        ==================================================================================
        ���ݿ����++
        > use runoob        --�������л����ݿ⣬�����ݿⲻ�����򴴽�
        switched to db runoob
        > db                --�鿴��ǰ���ݿ�
        runoob
        > show dbs          --�鿴���ݿ��б���runoob��δд������ʱ����������
        test   0.000GB
        local   0.000GB
        > db.runoob.insert({"name":"--"})   --runoob���ݿ��в�������
        WriteResult({ "nInserted" : 1 })
        > show dbs          --�鿴���ݿ��б�
        local   0.078GB
        runoob  0.078GB
        test    0.078GB
        > db.dropDatabase() --ɾ����ǰ���ݿ�
        ==================================================================================
        ����(�����)++
        ����������������
        { "dropped" : "runoob", "ok" : 1 }
        > show tables       --չʾ��ǰ���ݿ����м���
        site
        > db.site.drop()    --ɾ������
        true
        ����������������
        > use test
        switched to db test
        > db.createCollection("runoob")     --����runoob����
        { "ok" : 1 }
        ����������������
        > show collections  --չʾ���м���
        runoob
        system.indexes
        ����������������
        -capped : true      --�����̶����ϣ����ﵽ���ֵʱ�������Զ�����������ĵ���
                              ����ֵΪ true ʱ������ָ�� size ����
        -autoIndexId : true --�Զ��� _id �ֶδ���������Ĭ��Ϊ false
        -ע�⣺�ڲ����ĵ�ʱ��MongoDB ���ȼ��̶����ϵ� size �ֶΣ�Ȼ���� max �ֶ�
         ���� �̶����� mycol���������Ͽռ��С 6142800 KB, �ĵ�������Ϊ 10000 ��
        > db.createCollection("mycol", { capped : true, autoIndexId : true, size :
           6142800, max : 10000 } )
        { "ok" : 1 }
        ����������������
        ==================================================================================
        �ĵ����ݲ���++���ݲ���
        db.mycol2.insert({"name" : "�̳�"})   --mongo�ڲ����ĵ�ʱ���Զ���������
        ����������������
        > db.col.insert({title:'�̳�1'})      --�����ϲ�������
            WriteResult({ "nInserted" : 1 })
        > db.col.insert({title:'�̳�2'})
        > db.col.insert({title:'�̳�3'})
        > db.col.insert({title:'�̳�3'})
        > document=({title:'�̳�4'})          --��������
          {
            "title":"�̳�4"
          }
        >document
          {
             "title":"�̳�4"
          }
        >db.col.insert(document)              --�����������insert
        >db.col.save(document)                --�����������save
        ����������������
        3.2�汾��֧�ֶ�������
        >var document = db.collection.insertOne({"a": 3})
        >var res = db.collection.insertMany([{"b": 3}, {'c': 4}])
        ==================================================================================
        �ĵ����ݲ���++����(�ĵ�)���£�
        db.collection.update(
           <query>,     --update�Ĳ�ѯ����������sql update��ѯ��where�����
           <update>,    --update�Ķ����һЩ���µĲ���������$,$inc...���ȣ�Ҳ�������Ϊsql update��ѯ��set�����
           {
             upsert: <boolean>,         --���������update�ļ�¼���Ƿ����objNew,trueΪ���룬Ĭ����false��������
             multi: <boolean>,          --mongodb Ĭ����false,ֻ�����ҵ��ĵ�һ����¼���������Ϊtrue,�ͰѰ����������������¼ȫ������
             writeConcern: <document>   --�׳��쳣�ļ���
           }
        )
        > db.col.update({title:'�̳�'},{"title":"lisheng----"},{})
        > db.col.save({"_id" : ObjectId("56064f89ade2f21f36b03136"),"title" : "MongoDB"})
            --��������id�滻�ĵ�����
        ֻ���µ�һ����¼��
        db.col.update( { "count" : { $gt : 1 } } , { $set : { "test2" : "OK"} } );
        ȫ�����£�
        db.col.update( { "count" : { $gt : 3 } } , { $set : { "test2" : "OK"} },false,true );
        ֻ��ӵ�һ����
        db.col.update( { "count" : { $gt : 4 } } , { $set : { "test5" : "OK"} },true,false );
        ȫ����Ӽӽ�ȥ:
        db.col.update( { "count" : { $gt : 5 } } , { $set : { "test5" : "OK"} },true,true );
        ȫ�����£�
        db.col.update( { "count" : { $gt : 15 } } , { $inc : { "count" : 1} },false,true );
        ֻ���µ�һ����¼��


        db.col.update( { "count" : { $gt : 10 } } , { $inc : { "count" : 1} },false,false );
         ����������������
        ���µ����ĵ�a
        > db.test_collection.updateOne({"name":"abc"},{$set:{"age":"28"}})
        ���¶���ĵ�
        > db.test_collection.updateMany({"age":{$gt:"10"}},{$set:{"status":"xyz"}})
        ==================================================================================
        �ĵ����ݲ���++����(�ĵ�)ɾ����
        db.collection.remove(
           <query>,                   query :����ѡ��ɾ�����ĵ���������
           {
             justOne: <boolean>,      justOne : ����ѡ�������Ϊ true �� 1����ֻɾ��һ���ĵ���
             writeConcern: <document> writeConcern :����ѡ���׳��쳣�ļ���
           }
        )
        ɾ��������ȫ���ĵ���
        db.inventory.deleteMany({})
        ɾ�� status ���� A ��ȫ���ĵ���
        db.inventory.deleteMany({ status : "A" })
        ɾ�� status ���� D ��һ���ĵ���
        db.inventory.deleteOne( { status: "D" } )
