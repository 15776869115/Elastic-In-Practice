## ��47�ڣ���ʶ��������_search api�Ļ����﷨����

### 1��search api�Ļ����﷨

```json
GET /search
{}

GET /index1,index2/type1,type2/search
{}

GET /_search
{
  "from": 0,
  "size": 10
}
```



### 2��httpЭ����get�Ƿ���Դ���request body

HTTPЭ�飬һ�㲻����get�������request body��������Ϊget�����ʺ�������ѯ���ݵĲ�������˻�����ô����

```json
GET /_search?from=0&size=10

POST /_search
{
  "from":0,
  "size":10
}
```

���ɣ��ܶ�������������Ƿ�������Ҳ��֧��GET+request bodyģʽ

���������֧�ֵĳ�����Ҳ������POST /_search