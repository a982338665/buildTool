
### ���ֲ������췽����

    ��ע���ʶ��@nonNull�ֶΣ�Ȼ���Ը��ֶ�ΪԪ�ز���һ�����캯������ע����������ֶζ�û��@nonNullע�⣬��Ч��ͬNoArgsConstructor

**1.ʾ��1��**

    @RequiredArgsConstructor
    public class Demo {
        private final int finalVal = 10;
        @NonNull
        private String name;
        @NonNull
        private int age;
    }
    �����
    public class Demo {
        private final int finalVal = 10;
        @NonNull
        private String name;
        @NonNull
        private int age;
        public Demo(@NonNull String name, @NonNull int age) {
            if (name == null) {
                throw new NullPointerException("name is marked @NonNull but is null");
            } else {
                this.name = name;
                this.age = age;
            }
        }
    }
    ����1��
        ��ע���ʶ��@nonNull�ֶΣ�Ȼ���Ը��ֶ�ΪԪ�ز���һ�����캯������ע����������ֶζ�û��@nonNullע�⣬��Ч��ͬNoArgsConstructor
        

