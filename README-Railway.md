# 在Railway.app上部署RAGFlow
ECHO is off.
这个文档包含在Railway.app上部署RAGFlow的说明。
ECHO is off.
## 部署步骤
ECHO is off.
1. 登录Railway.app (https://railway.app/)
2. 点击"New Project"按钮
3. 选择"Deploy from GitHub repo"
4. 连接您的GitHub账号（如果尚未连接）
5. 选择您Fork的RAGFlow仓库
6. 在环境变量部分，添加以下变量：
   - OPENAI_API_KEY: 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
   - OPENAI_API_BASE: https://openrouter.ai/api/v1
   - OPENAI_API_MODEL: qwen/qwq-32b:free
   - ES_HOST: disabled
   - MYSQL_HOST: disabled
   - MINIO_HOST: disabled
   - REDIS_HOST: disabled
   - INFINITY_HOST: disabled
   - DISABLE_ES: true
   - DISABLE_MYSQL: true
   - DISABLE_MINIO: true
   - DISABLE_REDIS: true
   - DISABLE_INFINITY: true
7. 点击"Deploy"按钮
8. 等待部署完成（这可能需要几分钟）
9. 在"Settings"标签页中找到您的应用URL
10. 更新Edurora项目中的ragflowService.ts文件，使用您的Railway应用URL
ECHO is off.
## 环境变量说明
ECHO is off.
- OPENAI_API_KEY: OpenRouter API密钥
- OPENAI_API_BASE: OpenRouter API基础URL
- OPENAI_API_MODEL: 使用的模型名称
- ES_HOST, MYSQL_HOST, MINIO_HOST, REDIS_HOST, INFINITY_HOST: 设置为"disabled"以禁用这些服务的连接尝试
- DISABLE_ES, DISABLE_MYSQL, DISABLE_MINIO, DISABLE_REDIS, DISABLE_INFINITY: 设置为"true"以完全禁用这些服务

## 注意事项
ECHO is off.
Railway.app不支持多容器部署，因此我们需要禁用RAGFlow中的一些依赖服务。这种配置下，RAGFlow将只使用OpenRouter API进行文本生成，而不使用其他高级功能（如文档索引和搜索）。

## 更新日志
ECHO is off.
- 2025-03-14: 初始版本
- 2025-03-15: 测试Git凭据管理器
