
#���ֽ��springboot ��������ķ���ʾ��

##1.ȫ������

    /**
     * ȫ�ֿ�����
     * @author Boolean
     *
     */
    @Configuration
    public class CorsConfig {
        private CorsConfiguration buildConfig() {  
            CorsConfiguration corsConfiguration = new CorsConfiguration();  
            corsConfiguration.addAllowedOrigin("*"); // 1�����κ�����ʹ��
            //corsConfiguration.addAllowedOrigin("http://www.test.com"); // 1�����ض�����ʹ��
            corsConfiguration.addAllowedHeader("*"); // 2�����κ�ͷ
            corsConfiguration.addAllowedMethod("*"); // 3�����κη�����post��get�ȣ� 
            return corsConfiguration;  
        }  
      
        @Bean  
        public CorsFilter corsFilter() {  
            UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();  
            source.registerCorsConfiguration("/**", buildConfig()); // 4  
            return new CorsFilter(source);  
        } 
    }
    
 ##2.ע��
 
    ��ʽ��׼ȷ�����������˵��Ϊ�鷳����������������ÿ����Ҫ����Ľӿ���ʹ��@CrossOriginע�⡣
    @CrossOrigin(allowCredentials = "true", allowedHeaders = "*", origins = "*")
    allowCredentials(true)���������cookie���û�ƾ֤���ݣ�Ĭ��Ϊfalse��
