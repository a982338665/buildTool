

**1.�洢����������**

**2.mybatis���ô洢���̣�**

    dao:
         /**
           * ʹ�ô洢����ִ����ɱ
           * @param param
           */
          void killByProceduce(Map<String, Object> param);
    mapper:
        
        <!--mybatis���ô洢����,ԓ��д�ı����д-->
        <select id="killByProceduce" statementType="CALLABLE">
            CALL excute_seckill(
                    #{seckillId,jdbcType=BIGINT,mode=IN},
                    #{phone,jdbcType=BIGINT,mode=IN},
                    #{killTime,jdbcType=TIMESTAMP,mode=IN},
                    #{result,jdbcType=INTEGER,mode=OUT}
            );
        </select>
