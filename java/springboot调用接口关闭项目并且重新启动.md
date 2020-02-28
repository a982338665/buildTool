
###1.ҵ�񳡾���

    Ŀ�ģ�ͨ���ӿڵ���������Ŀ,�����±���javaԴ�ļ������¼���class

###2.����ʵ�֣�
####2.1׼���������������� (����ģʽ)
    
    package org.common.cutil;
    
    import lombok.Data;
    import org.springframework.context.ConfigurableApplicationContext;
    
    import java.io.File;
    import java.io.IOException;
    import java.util.concurrent.ArrayBlockingQueue;
    import java.util.concurrent.ExecutorService;
    import java.util.concurrent.ThreadPoolExecutor;
    import java.util.concurrent.TimeUnit;
    
    /**
     * ��Ŀ����������
     */
    @Data
    public class RestartUtil1 {
    
        private static RestartUtil1 restartUtil = new RestartUtil1();
    
        private ConfigurableApplicationContext configurableApplicationContext;
        private Class start;
        private String[] args;
        private boolean isRestart = false;
    
        private RestartUtil1() {
        }
    
        public static RestartUtil1 getInstance() {
            return restartUtil;
        }
    
        public void restart() {
            ExecutorService threadPool = new ThreadPoolExecutor(1, 1, 0,
                    TimeUnit.SECONDS, new ArrayBlockingQueue<>(1), new ThreadPoolExecutor.DiscardOldestPolicy());
            threadPool.execute(() -> {
                //�رշ��񣬴��ַ�ʽ�رշ��񲻻��ͷ��ڴ棬�ᵼ���ڴ治��
                while (configurableApplicationContext.isActive()) {
                    configurableApplicationContext.close();
                }
                System.err.println("�����ѹر�...");
                try {
                    //�ر�����cmd
                    Process exec = Runtime.getRuntime().exec("taskkill /f /im cmd.exe");
                    while (exec.isAlive()) {
                        Thread.sleep(1000);
                        System.err.println("�ȴ�cmd�ر�...");
                    }
                    //���´��ڣ��ڵ�ǰ�ļ����£�ִ������mvn
                    Runtime.getRuntime().exec("cmd  /c start mvn spring-boot:run", null, new File("./"));
                } catch (IOException e) {
                    e.printStackTrace();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            });
            threadPool.shutdown();
        }
    }

####2.2����springboot�������ࣩ

    package org.jingniu;
    
    import org.common.cutil.RestartUtil;
    import org.springframework.boot.SpringApplication;
    import org.springframework.boot.autoconfigure.SpringBootApplication;
    import org.springframework.context.ConfigurableApplicationContext;
    import org.springframework.stereotype.Component;
    
    @SpringBootApplication()
    @Component
    public class ASeckillApplication1 {
    
        public static void main(String[] args) {
            ConfigurableApplicationContext run = SpringApplication.run(
                    ASeckillApplication1.class, args);
            //�Ƿ�����
            restart(args, run);
        }
        private static void restart(String[] args, ConfigurableApplicationContext run) {
            RestartUtil.getInstance().setArgs(args);
            RestartUtil.getInstance().setRestart(true);
            RestartUtil.getInstance().setConfigurableApplicationContext(run);
            RestartUtil.getInstance().setStart(ASeckillApplication1.class);
        }
    }
####2.3ʹ�ã�
    
    package org.common.cweb;
    
    import org.common.cutil.RestartUtil;
    import org.common.cutil.Result;
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RequestMethod;
    import org.springframework.web.bind.annotation.ResponseBody;
    
    @Controller
    @RequestMapping("/test")
    public class NBTestController1 {
    
        @RequestMapping(value = "/test", method = RequestMethod.POST)
        @ResponseBody
        public Result list() {
            RestartUtil instance = RestartUtil.getInstance();
            if (instance.getRestart()) instance.restart();
            return Result.success(0);
        }
    }
  
 
    
###final.���������������⣺
    
    1.��Ŀ��������ԭ�����ڴ�δ���ͷţ������Դ��ڣ�����java�����ۻ�����ʹ�ڴ治��
        ������룺
            ExecutorService threadPool = new ThreadPoolExecutor(1, 1, 0,
                            TimeUnit.SECONDS, new ArrayBlockingQueue<>(1), new ThreadPoolExecutor.DiscardOldestPolicy());
                    threadPool.execute(() -> {
                        //�رշ��񣬴��ַ�ʽ�رշ��񲻻��ͷ��ڴ棬�ᵼ���ڴ治��
                        while (configurableApplicationContext.isActive()){
                            configurableApplicationContext.close();
                        }
                        System.err.println("�����ѹر�...");
                        //���������󣬻ᷢ��ԭ���Ľ��̲�δ��kill
                        ConfigurableApplicationContext configurableApplicationContext2 = SpringApplication.run(start, args);
                        this.configurableApplicationContext = configurableApplicationContext2;
                    });
                    threadPool.shutdown();
