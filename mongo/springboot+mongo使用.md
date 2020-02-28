
#https://docs.spring.io/spring-data/jpa/docs/current/reference/html/
#CSDN
##1.MongoRepository-QueryByExampleExecutor

    1. �̳�MongoRepository
        public interface StudentRepository extends MongoRepository<Student, String> {
        }
    2. ����ʵ��
        ʹ��ExampleMatcherƥ����-----ֻ֧���ַ�����ģ����ѯ��������������ȫƥ��
        Example��װʵ�����ƥ����
        ʹ��QueryByExampleExecutor�ӿ��е�findAll����
        ���ƴ���
        public Page<Student> getListWithExample(StudentReqVO studentReqVO) {
            Sort sort = Sort.by(Sort.Direction.DESC, "createTime");
            Pageable pageable = PageRequest.of(studentReqVO.getPageNum(), studentReqVO.getPageSize(), sort);
            Student student = new Student();
            BeanUtils.copyProperties(studentReqVO, student);
            //����ƥ�����������ʹ�ò�ѯ����
            ExampleMatcher matcher = ExampleMatcher.matching() //��������
                    .withStringMatcher(ExampleMatcher.StringMatcher.CONTAINING) //�ı�Ĭ���ַ���ƥ�䷽ʽ��ģ����ѯ
                    .withIgnoreCase(true) //�ı�Ĭ�ϴ�Сд���Է�ʽ�����Դ�Сд
                    .withMatcher("name", ExampleMatcher.GenericPropertyMatchers.contains()) //���á�����ƥ�䡱�ķ�ʽ��ѯ
                    .withIgnorePaths("pageNum", "pageSize");  //�������ԣ��������ѯ
        
            //����ʵ��
            Example<Student> example = Example.of(student, matcher);
            Page<Student> students = studentRepository.findAll(example, pageable);
            return students;
        }
    3.ȱ�㣺���¶�֧��...
        //��֧�ֹ����������顣����֧�ֹ��������� or(��) �����ӣ����еĹ������������Ǽ�һ����� and(����) ����
        //��֧������ֵ�ķ�Χ��ѯ����ʱ�䷶Χ�Ĳ�ѯ
    4.������ѯ������
        1.��ѯ������
            long size = personRepository.count();
        2.����ʵ���������Բ�ѯ��
            find + By + ������������ĸ��д��
            Person person = personRepository.findByName(name);
        3.����ʵ�����е����Խ���ģ����ѯ��
            find + By + ������������ĸ��д�� + Like
            List<Person> person = personRepository.findByNameLike(name);
        4.����ʵ�����е����Խ���ģ����ѯ����ҳ��
            PageRequest pageRequest = new PageRequest(page-1,rows);
            List<Person> person = personRepository.findByNameLike(name, pageRequest).getContent();
        5.����ʵ�����е����Խ���ģ����ѯ����ҳ��ͬʱָ�����صļ������ݿ��е�key,ʵ�����е����ԣ���
            Ŀ�ģ�ֻ����Person�е�id��name��������age.
            PersonRepository����ӷ�����ͬʱʹ��ע��@Query
                 @Query(value="{'name':?0}",fields="{'name':1}")
                 public Page<Person> findByNameLike(String name,Pageable pageable);
                 ���ͣ�
                    value���ǲ�ѯ������
                    ?0:ռλ��-��Ӧ�ŷ����в����еĵ�һ������
                    ?1:ռλ��-��Ӧ�ŷ����в����еĵڶ�������
                    fields��������ָ���ķ����ֶΣ�����id���Զ����ص�
                    bson��{'name':1}��1����true��Ҳ���Ǵ����ص���˼��
            Service����PersonRepository��
                 PageRequest pageRequest = new PageRequest(page-1,rows);        
                 List<Person> person = personRepository.findByNameLike(name, pageRequest).getContent();
        6.��ѯ�������ݣ�ͬʱָ�����صļ�:
            ע�⣺
                ��ָ�����صļ�ʱ������ʹ�òֿ����Դ���findAll��������
                ����ѯ����id��Ϊ�յ����ݣ�ͬʱָ�����صļ�
            find + By + ������������ĸ��д�� + NotNull
            �ֿ⣺
                @Query(value="{'_id':{'$ne':null}}",fields="{'name':1}")
                public Page<Person> findByIdNotNull(Pageable pageable);
            service:
                PageRequest pageRequest = new PageRequest(page-1,rows);    
                List<Person> person = personRepository.findByIdNotNull(pageRequest).getContent();
        7.������
             GreaterThan(����) 
             ������������findByAgeGreaterThan(int age) 
             query�е�value������{"age" : {"$gt" : age}}
     
             LessThan��С�ڣ� 
             ������������findByAgeLessThan(int age) 
             query�е�value������{"age" : {"$lt" : age}}
     
             Between����...֮�䣩 
             ������������findByAgeBetween(int from, int to)  
             query�е�value������{"age" : {"$gt" : from, "$lt" : to}}
            
             Not���������� 
             ������������findByNameNot(String name)
             query�е�value������{"age" : {"$ne" : name}}
            
             Near����ѯ����λ������ģ� 
             ������������findByLocationNear(Point point) 
             query�е�value������{"location" : {"$near" : [x,y]}}
        
##2.
