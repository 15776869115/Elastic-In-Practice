## 05-�ṹ������-�ڰ�����ʵսʹ��terms�������ֵ�Լ���ֵ��������Ż�

term: {"field": "value"}

terms: {"field": ["value1", "value2"]}

```sql
-- sql�е�in
select * from tbl where col in ("value1", "value2")
```



#### 1��Ϊ������������tag�ֶ�

```json
POST /forum/article/_bulk
{ "update": { "_id": "1"} }
{ "doc" : {"tag" : ["java", "hadoop"]} }
{ "update": { "_id": "2"} }
{ "doc" : {"tag" : ["java"]} }
{ "update": { "_id": "3"} }
{ "doc" : {"tag" : ["hadoop"]} }
{ "update": { "_id": "4"} }
{ "doc" : {"tag" : ["java", "elasticsearch"]} }
```



#### 2������articleIDΪKDKE-B-9947-#kL5��QQPX-R-3956-#aD8�����ӣ�����tag�а���java������

```json
GET /forum/article/_search 
{
  "query": {
    "constant_score": {
      "filter": {
        "terms": {
          "articleID": [
            "KDKE-B-9947-#kL5",
            "QQPX-R-3956-#aD8"
          ]
        }
      }
    }
  }
}

GET /forum/article/_search
{
    "query" : {
        "constant_score" : {
            "filter" : {
                "terms" : { 
                    "tag" : ["java"]
                }
            }
        }
    }
}
```



#### 3���Ż������������������tagֻ����java������

```jsn
POST /forum/article/_bulk
{ "update": { "_id": "1"} }
{ "doc" : {"tag_cnt" : 2} }
{ "update": { "_id": "2"} }
{ "doc" : {"tag_cnt" : 1} }
{ "update": { "_id": "3"} }
{ "doc" : {"tag_cnt" : 1} }
{ "update": { "_id": "4"} }
{ "doc" : {"tag_cnt" : 2} }
```



```json
GET /forum/article/_search
{
  "query": {
    "constant_score": {
      "filter": {
        "bool": {
          "must": [
            {
              "term": {
                "tag_cnt": 1
              }
            },
            {
              "terms": {
                "tag": ["java"]
              }
            }
          ]
        }
      }
    }
  }
}
```

["java", "hadoop", "elasticsearch"]



#### 4��ѧ����֪ʶ������

��1��terms��ֵ����
��2���Ż�terms��ֵ�����Ľ��
��3���൱��SQL�е�in���

