
### NonNull ������-���Լ�����

    ���ע�����ڷ����ϣ����Խ������еĴ�����try-catch�����������������쳣����catch����Lombok.sneakyThrow(e)���쳣�׳���
    ����ʹ��@SneakyThrows(Exception.class)����ʽָ���׳������쳣
    
**1.ʹ�ã�**

    @SneakyThrows(UnsupportedEncodingException.class)
       public String utf8ToString(byte[] bytes) {
           return new String(bytes, "UTF-8");
       }
    �����
    @SneakyThrows(UnsupportedEncodingException.class)
       public String utf8ToString(byte[] bytes) {
           try{
               return new String(bytes, "UTF-8");
           }catch(UnsupportedEncodingException uee){
               throw Lombok.sneakyThrow(uee);
           }
       }




