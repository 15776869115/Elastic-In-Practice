## 09-���̽����������-����boost��ϸ������������Ȩ�ؿ���

**����**�����������а���java�����ӣ�ͬʱ�أ���������а���hadoop��elasticsearch��**����**����������ͬʱ�أ����һ�����Ӱ���java hadoop��һ�����Ӱ���java elasticsearch������hadoop������Ҫ��elasticsearch**����**��������

**֪ʶ��**������������Ȩ�أ�boost�����Խ�ĳ������������Ȩ�ؼӴ󣬴�ʱ��ƥ���������������ƥ����һ������������document������relevance scoreʱ��ƥ��Ȩ�ظ��������������document��relevance score����ߣ���ȻҲ�ͻ����ȱ����ػ���

Ĭ������£�����������Ȩ�ض���һ���ģ�����1

```json
GET /forum/article/_search 
{
  "query": {
    "bool": {
      "must": [
        {
          "match": {
            "title": "blog"
          }
        }
      ],
      "should": [
        {
          "match": {
            "title": {
              "query": "java"
            }
          }
        },
        {
          "match": {
            "title": {
              "query": "hadoop"
            }
          }
        },
        {
          "match": {
            "title": {
              "query": "elasticsearch"
            }
          }
        },
        {
          "match": {
            "title": {
              "query": "spark",
              "boost": 5
            }
          }
        }
      ]
    }
  }
}
```
