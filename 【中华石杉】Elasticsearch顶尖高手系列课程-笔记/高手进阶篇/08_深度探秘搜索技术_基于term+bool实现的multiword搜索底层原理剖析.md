## 08-���̽����������-����term+boolʵ�ֵ�multiword�����ײ�ԭ������

#### 1����ͨmatch���ת��Ϊterm+should

```json
{
    "match": { "title": "java elasticsearch"}
}
```



ʹ�����������match query���ж�ֵ������ʱ��es���ڵײ�**�Զ������match queryת��Ϊbool���﷨**
bool should��ָ����������ʣ�ͬʱʹ��term query

```json
{
  "bool": {
    "should": [
      { "term": { "title": "java" }},
      { "term": { "title": "elasticsearch"   }}
    ]
  }
}
```



#### 2��and match���ת��Ϊterm+must

```json
{
    "match": {
        "title": {
            "query":    "java elasticsearch",
            "operator": "and"
        }
    }
}
```

```json
{
  "bool": {
    "must": [
      { "term": { "title": "java" }},
      { "term": { "title": "elasticsearch"   }}
    ]
  }
}
```



#### 3��minimum_should_match���ת��

```json
{
    "match": {
        "title": {
            "query":                "java elasticsearch hadoop spark",
            "minimum_should_match": "75%"
        }
    }
}
```



```json
{
  "bool": {
    "should": [
      { "term": { "title": "java" }},
      { "term": { "title": "elasticsearch"   }},
      { "term": { "title": "hadoop" }},
      { "term": { "title": "spark" }}
    ],
    "minimum_should_match": 3 
  }
}
```



��һ����ΪɶҪ��������ʵ��multi-value�����ķ�ʽ�أ�ʵ���ϣ����Ǹ���һ�������̵�ġ�match query --> bool + term��


