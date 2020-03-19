
### Cleanup �ܹ��Զ��ͷ���Դ

    ���ע�����ڱ���ǰ�棬���Ա�֤�˱����������Դ�ᱻ�Զ��رգ�Ĭ���ǵ�����Դ��close()������
    �������Դ�������رշ�������ʹ��@Cleanup(��methodName��)��ָ��Ҫ���õķ���������������������ٸ����Ӱɣ�
    
**1.ʾ��1��**

    public static void main(String[] args) throws Exception {
            @Cleanup InputStream in = new FileInputStream(args[0]);
            @Cleanup OutputStream out = new FileOutputStream(args[1]);
            byte[] b = new byte[1024];
            while (true) {
                int r = in.read(b);
                if (r == -1) break;
                out.write(b, 0, r);
            }
        }
    �����
    public static void main(String[] args) throws Exception {
            FileInputStream in = new FileInputStream(args[0]);
    
            try {
                FileOutputStream out = new FileOutputStream(args[1]);
    
                try {
                    byte[] b = new byte[1024];
    
                    while(true) {
                        int r = in.read(b);
                        if (r == -1) {
                            return;
                        }
    
                        out.write(b, 0, r);
                    }
                } finally {
                    if (Collections.singletonList(out).get(0) != null) {
                        out.close();
                    }
    
                }
            } finally {
                if (Collections.singletonList(in).get(0) != null) {
                    in.close();
                }
    
            }
        }

    
