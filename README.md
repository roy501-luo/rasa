#Rasa项目基本流程

## 1.初始化项目
```docker run -v ${pwd}:/app rasa/rasa:3.1.2-full init --no-prompt```

## 2.准备NLLU训练数据
 ```/data/nlu.yml```

## 3.配置NLU模型
```rasa3.0 支持中文，demo阶段不用调整```

## 4.准备故事(story)数据
```/data/stories.yml```

## 5.定义域(domain)
```./domain.yml```

## 6.配置 Rasa Core 模型
```./config.yml```

## 7.训练机器人
```
docker run -v ${pwd}:/app rasa/rasa:3.1.2-full train --domain domain.yml --data data\ --out models
```

## 8.测试机器人
```
docker run -ti -v ${pwd}:/app rasa/rasa:3.1.2-full shell
```

## 9.让用户使用机器人
https://rasa.com/docs/rasa/connectors/your-own-website
```
docker run -v C:\\Users\\roy\\IdeaProjects\\rasa:/app rasa/rasa:3.1.2-full run --enable-api --cors “*”
```

开启rasa-api后，即可通过post请求发送消息
post http://<host>:<port>/webhooks/rest/webhook
```json
{
  "sender": "test_user",
  "message": "Hi there!"
}
```
返回
```json
[
  {"text": "Hey Rasa!"}, {"image": "http://example.com/image.jpg"}
]
```
