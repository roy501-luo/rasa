# 初始化Rasa项目
docker run -v C:\\Users\\roy\\IdeaProjects\\rasa:/app rasa/rasa:3.1.2-full init --no-prompt

# 访问Rasa助手
docker run -ti -v C:\\Users\\roy\\IdeaProjects\\rasa:/app rasa/rasa:3.1.2-full shell

# 训练模型
docker run -v C:\\Users\\roy\\IdeaProjects\\rasa:/app rasa/rasa:3.1.2-full train --domain domain.yml --data data\ --out models

# 重启应用新模型
docker run -v C:\\Users\\roy\\IdeaProjects\\rasa:/app rasa/rasa:3.1.2-full run --enable-api --cors “*”