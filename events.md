# SSE 事件通知

<!-- toc -->

## GET /v2/zone/{zone}/notifier/stream

**SSE 事件通知**

### 请求

#### QueryString 参数

`NULL`

### 服务端响应

|事件类型|示意|
|----|----|
|message|业务事件通知|
|hb|心跳维持(客户端无需处理)|

#### 响应头信息

`NULL`

#### 响应 Body 信息

```
event:message
data:{"job_id":"eca24266-70f5-4127-829a-645f7362cb3b","action":"StartInstances","request_id":"535fa5b6-e649-4d2f-874e-4cb0768ce263","status":"pending","create_time":"2016-08-17T06:59:34Z","begin_time":"","finished_time":"","extra":"","zone":"ac2","resource_ids":null}

event:message
data:{"job_id":"eca24266-70f5-4127-829a-645f7362cb3b","action":"StartInstances","request_id":"535fa5b6-e649-4d2f-874e-4cb0768ce263","status":"working","create_time":"2016-08-17T06:59:34Z","begin_time":"2016-08-17T06:59:35Z","finished_time":"","extra":"","zone":"ac2","resource_ids":[]}

event:hb
data:hb
```

### 示例

#### 发送请求

```bash
$ curl -XGET  "http://dev2.51idc.cn:9000/v2/zone/ac2/notifier/stream"
```

#### 响应内容:

```
event:hb
data:❤️

event:message
data:{"job_id":"a1025ede-e569-4b10-84df-1c709cc3e01e","action":"StartInstances","request_id":"ba8b5cde-8362-4cac-ad5c-54fb4f641827","status":"pending","create_time":"2016-08-17T07:04:31Z","begin_time":"","finished_time":"","extra":"","zone":"ac2","resource_ids":null}

event:message
data:{"job_id":"a1025ede-e569-4b10-84df-1c709cc3e01e","action":"StartInstances","request_id":"ba8b5cde-8362-4cac-ad5c-54fb4f641827","status":"working","create_time":"2016-08-17T07:04:31Z","begin_time":"2016-08-17T07:04:31Z","finished_time":"","extra":"","zone":"ac2","resource_ids":[]}

event:hb
data:❤️

....

```



## GET /v2/zone/{zone}/unfinished_jobs

**读取未完成 JOB 列表**

### 请求参数

`NULL`

### 服务端响应

#### 响应 Body 信息

`Job 数组`

### 示例

#### 发送请求

```bash
$ curl -XGET  "http://dev2.51idc.cn:9000/v2/zone/ac2/notifier/stream"
```

#### 响应内容:

```
[
  {
    "job_id": "a7163fa5-0197-4ee9-81aa-b42bb7526392",
    "action": "AttachVolumes",
    "request_id": "dc29ea11-27cd-465f-8848-ad7f8a452c00",
    "status": "working",
    "create_time": "2016-08-17T10:07:02Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
  },
  {
    "job_id": "3dfeada1-760a-4ffb-a5c2-8d801adc209b",
    "action": "RunInstances",
    "request_id": "dc29ea11-27cd-465f-8848-ad7f8a452c00",
    "status": "working",
    "create_time": "2016-08-17T10:06:52Z",
    "begin_time": "2016-08-17T10:06:52Z",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
  }
]

```

