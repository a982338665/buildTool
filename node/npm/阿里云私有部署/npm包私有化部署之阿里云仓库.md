
## ����
    
    1.20200818��Ŀǰ�ڹ���
    2.���⣺ֻ��ά�����һ���汾
    3.�����ĵ���https://help.aliyun.com/document_detail/67306.html?spm=a2c4g.11186623.6.580.7d76c95cVqZYOh
    3.ע�⣺
        ���ϴ�ʱ��������403���⣬��鿴�Ƿ�Ϊ�汾δ���������¸��Ǳ���
            npm login --registry=https://registry-node.aliyun.com/org/1170113524267117/registry/kinovoreport/
            package.json:
                "name": "@kinovo-report-api/report-api",
                  "version": "1.0.9",
                  "private": false,
                  "bin": {
                    "report": "bin/report"
                  },
                  "publishConfig": {
                    "registry": "https://registry-node.aliyun.com/org/1170113524267117/registry/kinovoreport/"
                  },
            npm publish
        ������ʱ��
            mkdir code/
            cd code/
            cp /.npmrc code/
            npm i -loglevel info @kinovo-report-api/report-api@1.0.9
        ��.npmrc�ļ�:�е�auth
            echo -n 'myuser:mypassword' | openssl base64
