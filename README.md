# JadeAI LazyCat Cloud App

JadeAI 的懒猫微服应用封装。

## 应用配置

### 设置向导参数

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `auth_enabled` | bool | false | 是否启用用户认证 |
| `auth_secret` | secret | - | JWT 签名密钥 |
| `google_client_id` | string | - | Google OAuth 客户端 ID |
| `google_client_secret` | secret | - | Google OAuth 客户端密钥 |
| `db_type` | string | sqlite | 数据库类型 (sqlite/postgresql) |
| `default_locale` | string | zh | 默认语言 (zh/en/ja) |

### 环境变量说明

应用支持以下环境变量，已在 LazyCat manifest 中配置：

- `APP_NAME` - 应用名称
- `AUTH_ENABLED` - 认证开关
- `AUTH_SECRET` - JWT 密钥
- `GOOGLE_CLIENT_ID` - Google OAuth ID
- `GOOGLE_CLIENT_SECRET` - Google OAuth 密钥
- `DB_TYPE` - 数据库类型
- `SQLITE_PATH` - SQLite 数据库路径 (/app/data/jade.db)
- `DEFAULT_LOCALE` - 默认语言

## 构建和发布

### 前置要求

- lzc-cli v2.0.0+
- npm install -g @lazycatcloud/lzc-cli@2.0.0

### 构建

```bash
lzc-cli project build -o jadeai.lpk
```

### 复制镜像（需要先登录）

```bash
lzc-cli appstore copy-image twwch/jadeai:latest
# 记录返回的镜像地址
```

### 更新镜像地址

将 `lzc-manifest.yml` 中的镜像地址更新为复制后的地址。

### 发布

```bash
lzc-cli project build -o jadeai-1.0.0.lpk
lzc-cli appstore publish jadeai-1.0.0.lpk
```

## 目录说明

- `package.yml` - 应用静态元数据
- `lzc-manifest.yml` - 运行时配置
- `lzc-deploy-params.yml` - 安装向导配置
- `lzc-build.yml` - 构建配置
