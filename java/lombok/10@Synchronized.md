
### NonNull ������-���Լ�����

    ���ע�������෽������ʵ�������ϣ�Ч����synchronized�ؼ�����ͬ����������������ͬ�������෽����ʵ��������
    synchronized�ؼ��ֵ�������ֱ������class�����this���󣬶�@Synchronized��������ֱ���˽�о�̬final����LOCK��˽��final����lock��
    ��Ȼ��Ҳ�����Լ�ָ��������
    
**1.ʹ�ã�**

    @Synchronized
        public static void hello() {
            System.out.println("world");
        }
    
        @Synchronized
        public int answerToLife() {
            return 42;
        }
    
        @Synchronized("readLock")
        public void foo() {
            System.out.println("bar");
        }

    �����
    
    public static void hello() {
            Object var0 = $LOCK;
            synchronized($LOCK) {
                System.out.println("world");
            }
        }
    
        public int answerToLife() {
            Object var1 = this.$lock;
            synchronized(this.$lock) {
                return 42;
            }
        }
    
        public void foo() {
            Object var1 = this.readLock;
            synchronized(this.readLock) {
                System.out.println("bar");
            }
        }





