
### @ToString/@EqualsAndHashCode

    ����toString��equals��hashcode������ͬʱ���߻�������һ��canEqual�����������ж�ĳ�������Ƿ��ǵ�ǰ���ʵ��
    @Generated����ʱò��ûʲô��
    @Getter/@Setter
    ��һ��ע��������Ͼͺܺ���⣬���ڳ�Ա����������������棬�൱��Ϊ��Ա�������ɶ�Ӧ��get��set������ͬʱ������Ϊ���ɵķ���ָ���������η�����Ȼ��Ĭ��Ϊpublic
    ������ע��ֱ���������ϣ�����Ϊ����������зǾ�̬��Ա�������ɶ�Ӧ��get��set�����������final�������Ǿ�ֻ����get����
    
**1.ʹ�ã�**

    @ToString(
            includeFieldNames = true, //�Ƿ�ʹ���ֶ���
            exclude = {"name"}, //�ų�ĳЩ�ֶ�
            of = {"age"}, //ֻʹ��ĳЩ�ֶ�
            callSuper = true //�Ƿ��ø����ֶ�Ҳ���� Ĭ��false
    )



