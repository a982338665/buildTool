
### NonNull

    �����ķǿռ��
    
**1.ʹ�ã�**

    //��Ա������������@NonNullע��
    public String getName(@NonNull Person p){
        return p.getName();
    }
    �����
    public String getName(@NonNull Person p){
        if(p==null){
            throw new NullPointerException("person");
        }
        return p.getName();
    }



