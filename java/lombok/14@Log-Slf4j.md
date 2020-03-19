
### @Slf4j ����

    private static final org.slf4j.Logger log = org.slf4j.LoggerFactory.getLogger(LogExample.class);

**1.ʹ�ã�**
    
    @Slf4j
    class Parent {
    }
    �����
    class Parent {
        private static final Logger log = LoggerFactory.getLogger(Parent.class);
    
        Parent() {
        }
    }
    
    
    @Slf4j
    @CommonsLog(topic = "commonLog")
    class Parent {
    }
    �����
    class Parent {
        private static final Logger log = LoggerFactory.getLogger("commonLog");
    
        Parent() {
        }
    }








