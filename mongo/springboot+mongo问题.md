



##1.��ȡ_id�����ֶ�ʱ��
  
    ���⣺
        Ϊ�˻�ȡÿ�����ݵ�"_id"�ֶ�ʱ��ʹ����@Field("_id")ע����Ϊ����,readʱ��û����
        MongoRepository��insert�������л�ʧ�ܣ������쳣��Required identifier property not found for class����
    ���������    
        ��ע��@Id�滻@Field
##2.insertʱ����ʹ��mongo�Զ�����_id,�ڳ�����д��
 
    ObjectId objectId = new ObjectId();
    intent.setIntentId(objectId.toString());
    return intentRepository.insert(intent);
              

