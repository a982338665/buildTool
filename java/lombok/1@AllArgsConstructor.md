
### �������в����Ĺ��췽����

    1.����ָ�����ɵĹ��췽���ķ���Ȩ�ޣ�����ָ������һ����̬����
    ����1��
            ��@AllArgsConstructor���������в����Ĺ����������ᶪʧ�޲ι��캯��
            ��final������ֵ���ǲ���Ž����캯�������
    ����2��
            ��@AllArgsConstructor(access = AccessLevel.PRIVATE)    --�����ɾ�̬����
                ָ�����ɵĹ������ķ���Ȩ��Ϊprivate
            ��@AllArgsConstructor(access = AccessLevel.PROTECTED, staticName = "test") --���ɾ�̬����
                �����ɾ�̬��������Ĭ��ָ�����ɹ������ķ���Ȩ��Ϊprivate��
                ��������һ����̬����������ֵΪ�ù����������������Ķ���

**1.ʾ��1��**

    @AllArgsConstructor
    public class Parent {
    	private final int finalVal = 10;
        private Integer id;
    }
    �����
    public class Parent {
    	private final int finalVal = 10;
        private Integer id;
        public Parent(Integer id) {
            this.id = id;
        }
    }
    ����1��
        ��@AllArgsConstructor���������в����Ĺ����������ᶪʧ�޲ι��캯��
        ��final������ֵ���ǲ���Ž����캯�������
        
**2.ʾ��2��**

    @AllArgsConstructor(access = AccessLevel.PROTECTED, staticName = "test")
    public class Demo {
        private int age;
    }
    �����
    public class Demo {
        private int age;
        private Demo(int age) {
            this.age = age;
        }
        protected static Demo test(int age) {
            return new Demo(age);
        }
    }
    ����2��
        ��@AllArgsConstructor(access = AccessLevel.PRIVATE)    --�����ɾ�̬����
            ָ�����ɵĹ������ķ���Ȩ��Ϊprivate
        ��@AllArgsConstructor(access = AccessLevel.PROTECTED, staticName = "test") --���ɾ�̬����
            �����ɾ�̬��������Ĭ��ָ�����ɹ������ķ���Ȩ��Ϊprivate��
            ��������һ����̬����������ֵΪ�ù����������������Ķ���
            

    
