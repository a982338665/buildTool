
### @Val ��ǿ�������ƶ� varע�⣬��Java10֮��Ͳ���ʹ����

    �����Java10���Var����ǿ��������ƶϡ����Ҳ���ʹ����ȫ�ֱ����ϣ�ֻ��ʹ���ھֲ������Ķ����С�
    
**1.ʹ�ã�**

    class Parent {
    
        //private static final val set = new HashSet<String>(); //���벻ͨ��
    
        public static void main(String[] args) {
            val set = new HashSet<String>();
            set.add("aa");
            System.out.println(set); //[aa]
        }
    
    }

    �����
    
    class Parent {
        Parent() {
        }
    
        public static void main(String[] args) {
            HashSet<String> set = new HashSet();
            set.add("aa");
            System.out.println(set);
        }
    }






