# Launch Sheet Generator

## Overview

Generate a production launch sheet for the current feature branch. This document will be used for deployment to the production environment and should contain all necessary configuration, database, and service changes.

## Steps

* [ ] Compare current feature branch and origin/main branch to extract the differences.
* [ ] Check `config/config.ci.yaml` for configuration changes. Note that this file is only for CI testing, for production deployment, we need to use placeholders for sensitive information like credentials, etc
* [ ] Check `config/init_ci_data.sql` for database DDL changes. If new columns or new constraints are added, we need to use 'ALTER TABLE...' statements to add them to the database. We don't need to add data to the database, only the schema changes are needed.
* [ ] If there are new database records for table `dynamic_config`, we need specifiy the key and value in the '管理后台 - 动态配置' section. Those records can be added manually by admin users.

## Format

the launch sheet should be a markdown file with the following sections:
Note that, for '服务', we only need a `### 1.2. 服务` placeholder, no need to list all services.

for '数据库', remove all charset and collation related statements.

## 1. 上线单

### 1.1. 配置文件
```yaml
HttpConfig:
  ListenAddr: "0.0.0.0:8080"
  ApiKey: "{{API_KEY_PLACEHOLDER}}"
```

### 1.2. 数据库
```sql
CREATE TABLE whatever (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

ALTER TABLE existing_table 
ADD COLUMN new_column VARCHAR(255) NOT NULL;
```

### 1.3. 动态配置
* Key: `key_1`
* Value:
```json
{
    "config_key_1": "config_value_1",
}
```


### 1.4. 服务 
agent-manager
platform-web