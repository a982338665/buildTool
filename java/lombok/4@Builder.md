
### Builder �ṩ��һ�ֱȽ��Ƴ�Ĺ���ֵ����ķ�ʽ

    �ǳ��Ƽ���һ�ֹ���ֵ����ķ�ʽ��ȱ����Ǹ�������Բ��ܲ���builder
    
**1.ʾ��1��**

    @Builder
    public class Demo {
        private final int finalVal = 10;
    
        private String name;
        private int age;
    }
    �����
    public class Demo {
        private final int finalVal = 10;
        private String name;
        private int age;
    
        Demo(String name, int age) {
            this.name = name;
            this.age = age;
        }
    
        public static Demo.DemoBuilder builder() {
            return new Demo.DemoBuilder();
        }
    
        public static class DemoBuilder {
            private String name;
            private int age;
    
            DemoBuilder() {
            }
    
            public Demo.DemoBuilder name(String name) {
                this.name = name;
                return this;
            }
    
            public Demo.DemoBuilder age(int age) {
                this.age = age;
                return this;
            }
    
            public Demo build() {
                return new Demo(this.name, this.age);
            }
    
            public String toString() {
                String var10000 = this.name;
                return this.age;
            }
        }
    }
    ʹ�ã�
    public static void main(String[] args) {
           Demo demo = Demo.builder().name("aa").age(10).build();
           System.out.println(demo); 
       }

